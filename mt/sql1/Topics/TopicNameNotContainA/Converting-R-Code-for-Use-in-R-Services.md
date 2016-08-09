---
title: "Converting R Code for Use in R Services"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-31
ms.devlang: 
  - R
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: 12
manager: paulettm
---
# Converting R Code for Use in R Services
When you execute R code in the context of [!INCLUDE[ssNoersion]()], often the code will "just work" when added to the *@script* parameter of [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df).  
  
 However, often you should slightly modify the R script, both to take advantage of the integration with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], and to avoid expensive transfer of data. This topic provides guidance and examples of how you can convert R code from R code that you might run in an R IDE to a parameterized stored procedure that you can run in [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]  
  
## Tips on Converting R Code for Use in SQL  
 Keep in mind the following restrictions when converting your R code:  
  
 **Inputs and Outputs**  
  
-   All R data types are supported. However, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports a greater variety of data types than does R, so some implicit data type conversions are performed when sending [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data to R and vice versa. You might also need to explicitly cast or covert some data.  
  
     NULL values are supported. R uses the `na` data construct to represent missing values, which is similar to nulls.  
  
     For more information, see [Working with R Data Types](../../Topics/TopicNameNotContainA/Working-with-R-Data-Types.md).  
  
-   You can define a single input dataset as part of the stored procedure parameters. This input query for the stored procedure can be any valid single  SELECT statement. Stored procedure calls preceded by EXECUTE are not allowed.  
  
     All columns in the input must be mapped to variables in the R script. Variables are mapped automatically by name. For example, say your R script contains a formula like this one:  
  
    ```  
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek  
    ```  
  
     An error will be raised if the input dataset does not contains columns with the matching names ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour, and DayOfWeek.  
  
-   In [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], your R code is limited to outputting a single dataset as a data.frame object. However, you can also output multiple scalar outputs, including plots and models in varbinary format.  
  
     You can usually output the dataset returned by the R script without having to specify names of the output columns, by using the WITH RESULT SETS UNDEFINED option. However, any variables in the R script that you want to output must be mapped to SQL output parameters.  
  
     If you pass in variables as parameters of the stored procedure [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df), append the **OUTPUT** keyword to automatically include the parameter as a separate scalar output.  
  
-   You can provide multiple scalar parameters as input.  
  
## Restrictions  
 Keep in mind the following restrictions when converting your R code:  
  
-   All R data types are supported. However, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports a greater variety of data types than does R, so some implicit data type conversions are performed when sending [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data to R and vice versa. For more information, see [Working with R Data Types](../../Topics/TopicNameNotContainA/Working-with-R-Data-Types.md).  
  
-   The input query for the stored procedure can be any valid single  SELECT statement. To verify whether the SELECT statement is valid, try executing the query independently in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
-   NULL values are supported. R uses the `na` data construct to represent missing values, which is similar to nulls.  
  
-   Although R supports multiple outputs, in SQL Server2016 CTP3, only a single output dataset is supported. All columns in the output must be mapped to pre-defined R variable names.  
  
     Other constructs that return result sets, such as the OUTPUT clause, EXECUTE statement etc. are unsupported.  
  
-   You can provide multiple scalar parameters as input.  
  
## Example 1: Simple training and scoring  
 This example uses the airline dataset, which is included in the samples installed with [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], to illustrate the typical data science process.  To load this data into SQL  
  
#### To create the sample database  
  
1.  Create the database.  
  
    ```  
  
    CREATE DATABASE Airline  
    GO  
    ALTER DATABASE [Airline] SET RECOVERY SIMPLE WITH NO_WAIT  
    GO  
  
    ```  
  
2.  Create two tables.  
  
    ```  
  
    CREATE TABLE AirlineDemoSmallImport(  
    	ArrDelay varchar(100) NOT NULL, -- we start with varchar because missing values are coded as 'M'  
    	CRSDepTime float NOT NULL,  
    	DayOfWeek varchar(12) NOT NULL -- +2 for the quotes;   
    )  
    GO  
  
    CREATE TABLE AirlineDemoSmall(  
    	ArrDelay int NULL,  
    	CRSDepTime float NOT NULL,  
    	DayOfWeek varchar(10) NOT NULL  
    		CONSTRAINT CHK_DOW CHECK(DayOfWeek IN ('Monday','Tuesday','Wednesday','Thursday','Friday','Saturday','Sunday'))  
    )  
    GO  
  
    ```  
  
3.  Insert data from the .csv file into the table.  
  
    ```  
    BULK INSERT AirlineDemoSmallImport  
    FROM 'C:\Program Files\Microsoft SQL Server\MSSQL13\R_SERVICES\library\RevoScaleR\SampleData\AirlineDemoSmall.csv'  
    WITH (  
    	FIELDTERMINATOR = ',',  
    	ROWTERMINATOR = '\n',  
    	FIRSTROW = 2 -- Skip header  
    )  
    GO  
    IF (SELECT COUNT(*) FROM dbo.AirlineDemoSmallImport) <> 600000  
    BEGIN  
    	RAISERROR('Not all rows were imported.', 20, -1) WITH LOG  
    END  
    GO  
  
    ```  
  
4.  Update the table with a new feature column.  
  
    ```  
    INSERT INTO dbo.AirlineDemoSmall(ArrDelay, CRSDepTime, DayOfWeek)  
    SELECT   
    	CASE ArrDelay  
    		WHEN 'M' THEN NULL  
    		ELSE CONVERT(int, ArrDelay)  
    	END,  
    	CRSDepTime,  
    	REPLACE(DayOfWeek, '"', '')  
    FROM dbo.AirlineDemoSmallImport  
    GO  
    ```  
  
5.  Run a SELECT statement to verify that data is available.  
  
### Training a Model in R and in T-SQL  
 This R script gets 1 million rows of data from SQL Server, trains model using  `rxLinMod`, and writes the model back to the database.  
  
```  
# Load the serialization library  
source("serialization.r")  
  
# Define the transformation function used in modeling  
transformFunc <- function(data) {  
    data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))  
    return(data)  
}  
  
# Define the  variable to hold the transformed values  
transformVars <- c("CRSDepTime")  
  
# Specify the factor columns  
colInfo <- list(DayOfWeek = list(type="factor", levels=as.character(1:7)))  
  
# Specify the model formula  
  
formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek  
  
# Define the SQL query   
qq <- "select top 1000000 ArrDelay,CRSDepTime,DayOfWeek from airline"  
  
# Provide the connection string for the SQL Server instance  
# conStr <- paste("Driver={SQL Server};Server=.;Database=airline_new;Trusted_Connection=TRUE;",sep="")  
conStr <- "Driver={SQL Server};Server=.;Database=airline;Trusted_Connection=TRUE;"  
  
# Define the data source object and retrieve data from the database  
dsSqls <- RxSqlServerData(sqlQuery=qq, connectionString=conStr, colInfo=colInfo)  
  
# Define a new SQL Server compute context  
computeContext <- RxInSqlServer(numTasks=4, connectionString=conStr)  
  
# Train the model on the SQL Server instance  
mm <- rxLinMod(formula, data=dsSqls, transformFunc=transformFunc, transformVars=transformVars, computeContext=computeContext)  
  
# Display a summary of the trained model  
summary(mm)  
  
# Store the model in the database  
dbSaveRDS(conStr, "linmod.v1", mm)  
```  
  
### Scoring a Model Row by Row  
  
```  
# Load the library needed for Microsoft R Open if needed  
# require(RevoScaleR)  
  
source("serialization.r")  
  
# Create the connection string of the instance where the model is stored  
 conStr <- paste("Driver={SQL Server};Server=.;Database=airline;Trusted_Connection=TRUE;",sep="")  
  
# Load the model from the database  
mm <- dbReadRDS(conStr, "linmod.v1")  
  
# Prepare the data for single row scoring  
df <- data.frame(DayOfWeek=factor(2, levels=as.character(1:7)), CRSDepTime=21.53)  
  
# Call the rxPredict function   
pred <- rxPredict(mm, df)  
  
# Print the predictions to the R console  
print(pred)  
```  
  
 Some comment  
  
 In [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], you don't need to bring the data from the server to the local workspace, and you can write the results to a new table immediately.  
  
```  
-- Scoring for a single row of input values  
USE airline;  
  
---- Declare the SQL variable in which to store the model   
DECLARE @just_model varbinary(max);  
  
--- Get the model from the SQL table  
SELECT @just_model = [value] FROM [rmodels] WHERE [key] = 'linmod.v1';  
  
-- Set up the variable that will store the predicted value  
DECLARE @pred float;  
EXEC sp_execute_external_script  
   @language = N'R',  
   @script = N'  
         InputDataSet[,"DayOfWeek"] <- factor(InputDataSet[,"DayOfWeek"], levels=as.character(1:7))  
        mm <- unserialize(as.raw(model_param))  
  
         # Call rxPredict and write results to the default output data.frame  
         OutputDataSet <- rxPredict(mm, InputDataSet)  
   ',  
  
--- Specify the input data that is passed in to the model.   
--- Here values are hard-coded but you could write the stored procedure to accept input values as parameters.  
   @input_data_1 = N'select 2 as DayOfWeek, 21.53 as CRSDepTime',  
   @params = N'@model_param varbinary(max)',  
   @model_param = @just_model  
--- Define a single output column pred that contains the predicted value  
WITH RESULT SETS ((pred float));  
```  
  
 In the @params argument, you list all the SQL parameters tha tyou want ot use in the R code, except for the required parameters @input_data_1. In this case, there is only one parameter to the stored procedure  
  
### Scoring in Batch Mode  
  
## Example 2: Installing packages and calling multiple datasets  
 The following sample is slightly more complex. The source R code uses the RODBC package to get some additional data. It also needs the [e1071](https://cran.r-project.org/web/packages/e1071/index.html) package, which is not loaded by default.  
  
### Create a model using a new package  
  
```  
IrisPredict <- function(data, model){  
library(e1071)  
predicted_species <- predict(model, data)  
return(predicted_species)  
}  
  
library(RODBC)  
conn <- odbcConnect("MySqlAzure", uid = myUser, pwd = myPassword);  
Iris_data <-sqlFetch(conn, "Iris_Data");  
Iris_model <-sqlQuery(conn, "select model from my_iris_model");  
IrisPredict (Iris_data, model);  
  
```  
  
 assuming the e1071 package was enabled on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.  
  
```  
/* Input table schema */  
create table Iris_Data (name varchar(100), length int, width int);  
/* Model table schema */  
create table my_iris_model (model varbinary(max));  
  
declare @iris_model varbinary(max) = (select model from my_iris_model);  
exec sp_execute_external_script  
  @language = 'R'  
, @script = '  
IrisPredict <- function(data, model){  
library(e1071)  
predicted_species <- predict(model, data)  
return(predicted_species)  
}  
IrisPredict(input_data_1, model);  
'  
, @parallel = default  
, @input_data_1 = N'select * from Iris_Data'  
, @params = N'@model varbinary(max)'  
, @model = @iris_model  
with result sets ((name varchar(100), length int, width int, species varchar(30)));  
  
```  
  
 Notes:  
  
-   Error and status text returned from the R runtime as part of executing the e1071 library are returned to SQL as messages.  
  
-   Finally, the call to the stored procedure, [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df), is translated to a query tree that can be analyzed for performance and monitored like all other T-SQL queries.  
  
### Create a model using multiple data sources  
 This example demonstrates a slightly more complex query used as input to the model. Multiple calls are made to the R runtime, using different functions to train and then score an ARIMA model.  
  
```  
library(RODBC)  
ch <- odbcConnect("ChicagoCrimeAzure",uid="DemoUser", pwd="P@ssw0rd1")  
data <- sqlQuery(ch,"SELECT   
    dd.[Date] AS IncidentDate  
    ,SUM(sc.NumReports) AS NumIncidents  
  FROM DateDimension dd  
  LEFT JOIN SexCrimes sc  
  ON sc.IncidentDate = dd.[Date]  
  WHERE dd.[Date] BETWEEN '1/1/2001' AND (SELECT MAX(IncidentDate) FROM SexCrimes)  
  GROUP BY dd.[Date]  
  ORDER BY IncidentDate")  
data[["NumIncidents"]][is.na(data[["NumIncidents"]])] <- 0  
ld <- as.data.frame(sqlQuery(ch,"SELECT CAST(MAX([IncidentDate]) AS VARCHAR(10)) AS LastDate FROM SexCrimes;"))  
LastDate <- as.Date(as.POSIXct(as.character(ld$LastDate), origin="1970-01-01"))  
data_ts = ts(data$NumIncidents, start=c(2001,1),frequency=365)  
fit1 <- auto.arima(data_ts)  
train_model <- forecast(fit1,h=30)  
train_pred <- round(train_model$mean)  
data.forecast <- as.data.frame(t(train_pred))  
data.forecast <- as.data.frame(t(data.forecast))  
colnames(data.forecast) <- "PredictedCrimes"  
data.forecast["PredictedDate"] <- NA  
for(i in 1:30){data.forecast$PredictedDate[i] <- toString(LastDate + i)}  
data.forecast["CrimeCategory"] <- "Sex Crime"  
data.forecast;  
  
```  
  
 Notes:  
  
-   Note explaining code here  
  
-   Note explaining code here  
  
 The following code demonstrates how the same model could be trained and used for scoring in SQL Server with minimal modification:  
  
```  
declare @recent_date date = (SELECT CAST(MAX([IncidentDate]) AS VARCHAR(10)) AS LastDate FROM SexCrimes);  
exec sp_execute_external_script  
  @language = 'R'  
, @script = '  
library(forecast)  
data <- input_data_1  
data[["NumIncidents"]][is.na(data[["NumIncidents"]])] <- 0  
data_ts = ts(data$NumIncidents, start=c(2001,1),frequency=365)  
fit1 <- auto.arima(data_ts)  
train_model <- forecast(fit1,h=30)  
train_pred <- round(train_model$mean)  
data.forecast <- as.data.frame(t(train_pred))  
data.forecast <- as.data.frame(t(data.forecast))  
colnames(data.forecast) <- "PredictedCrimes"  
data.forecast["PredictedDate"] <- NA  
for(i in 1:30){data.forecast$PredictedDate[i] <- toString(LastDate + i)}  
data.forecast["CrimeCategory"] <- "Sex Crime"  
data.forecast;  
'  
, @input_data_1 = N'  
SELECT   
    dd.[Date] AS IncidentDate  
    ,SUM(sc.NumReports) AS NumIncidents  
  FROM DateDimension dd  
  LEFT JOIN SexCrimes sc  
  ON sc.IncidentDate = dd.[Date]  
  WHERE dd.[Date] BETWEEN '1/1/2001' AND (SELECT MAX(IncidentDate) FROM SexCrimes)  
  GROUP BY dd.[Date]  
  ORDER BY IncidentDate  
'  
, @params = N'@LastDate date'  
, @LastDate = @recent_date  
with result sets((name varchar(30), PredictedCrimes int, PredictedDate date, CrimeCategory varchar(30));  
  
```  
  
 Notes:  
  
-   Explain point in code above  
  
-   Explain point in code above