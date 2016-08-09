---
title: "Working with R Data Types"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5df99e1c-a89a-42c1-9d68-ffe8d9577c94
caps.latest.revision: 13
caps.handback.revision: 0
manager: paulettm
---
# Working with R Data Types
Whereas [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports several dozen  data types, R has a limited number of scalar data types (numeric, integer, complex, logical, character, date/time and raw). Therefore, when you use data from  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in R scripts, several different things can happen:  
  
-   Data is implicitly converted to a compatible data type.  
  
-   Data cannot be implicitly converted and an error is returned.  
  
 In general, whenever you have any doubt about how a particular data type or data structure is being used in R, use the  `str()` function to get the internal structure and type of the R object. The result of the function is printed to the R console and is also available in the query results, in the **Messages** tab in [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].  
  
 If a particular [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data type is not supported by R, but you need to use the columns of data in the R script, we recommend that you use the [CAST and CONVERT (Transact-SQL)](assetId:///a87d0850-c670-4720-9ad5-6f5a22343ea8) functions to ensure that the data type conversions are performed as intended before using the data in your R script.  
  
 For more information about [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data types, see [Data Types (Transact-SQL)](assetId:///a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4)  
  
## Data Type Conversion between R and SQL Server  
 The following table shows the changes in data types and values when data from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is used in an R script and then returned to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
|||||  
|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] type|R class|Type in **RESULT SET**|Comments|  
|**smalldatetime**|`POSIXct`|**datetime**|Represented as GMT|  
|**smallmoney**|`numeric`|**float**||  
|**datetime**|`POSIXct`|**datetime**|Represented as GMT|  
|**money**|`numeric`|**float**||  
|**uniqueidentifier**|`character`|**varchar(max)**||  
|**numeric(p,s)**|`numeric`|**float**||  
|**decimal(p,s)**|`numeric`|**float**||  
|**date**|`POSIXct`|**datetime**|Represented as GMT|  
|**tinyint**|`integer`|**int**||  
|**bit**|`logical`|**bit**||  
|**smallint**|`integer`|**int**||  
|**int**|`integer`|**int**||  
|**float**|`numeric`|**float**||  
|**real**|`numeric`|**float**||  
|**bigint**|`numeric`|**float**||  
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Only allowed as input parameter and output|  
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Only allowed as input parameter and output|  
|**varchar(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary(max)**|`raw`|**varbinary(max)**|Only allowed as input parameter and output|  
  
## Examples of Data Type Conversion  
 The following query gets a series of values from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table, and uses the stored procedure  [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df) to output the values using the R runtime .  
  
```  
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```  
  
 **Results**  
  
||||||  
|-|-|-|-|-|  
||C1|C2|C3|C4|  
|1|1|Hello|6e225611-4b58-4995-a0a5-554d19012ef1|4|  
|1|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|  
  
 Note the use of the `str` function in R to get the schema of the output data. This function returns the following information:  
  
```  
'data.frame':2 obs. of  4 variables:   
 $ c1: int  1 -11   
 $ c2: Factor w/ 2 levels "Hello","world": 1 2   
 $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1   
 $ cR: num  4 2  
```  
  
 From this, you can see that the following data type conversions were implicitly performed as part of this query:  
  
-   **Column C1**. The column is represented as **int** in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], `integer` in R, and **int** in the output result set.  
  
     No type conversion was performed.  
  
-   **Column C2**. The column is represented as **varchar(10)** in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], `factor` in R, and **varchar(max)** in the output.  
  
     Note how the output changes; any string from R (either a factor or a regular string) will be represented as **varchar(max)**, no matter what the length of the strings is.  
  
-   **Column C3**.  The column is represented as **uniqueidentifier** in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], `character` in R, and **varchar(max)** in the output.  
  
     Note the data type conversion that happens. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports the **uniqueidentifier** but R does not; therefore, the identifiers are represented as strings.  
  
-   **Column C4**. The column contains values generated by the R script and not present in the original data.