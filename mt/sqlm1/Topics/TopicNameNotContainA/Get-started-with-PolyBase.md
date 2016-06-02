---
title: Get started with PolyBase
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-polybase
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c71ddc50-b4c7-416c-9789-264671bd9ecb
---
# Get started with PolyBase
  This topic contains the basics about running PolyBase. For more information see [PolyBase Guide](../../Topics\TopicNameNotContainA/PolyBase-Guide.md).  
  
 After running the steps below, you will have:  
  
-   PolyBase installed and runnable on your server  
  
-   Examples of statements that create PolyBase objects  
  
-   An understanding of how to manage PolyBase objects in SQL Server Management Studio \(SSMS\)  
  
-   Examples of queries using PolyBase objects  
  
## Prerequisites  
 An instance of  [SQL Server \(64\-bit\)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016).  
  
-   Microsoft .NET Framework 4.5.  
  
-   Oracle Java SE RunTime Environment \(JRE\) version 7.51 or higher \(64\-bit\). Go to [Java SE downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html). The installer will fail if JRE is not present.  
  
-   Minimum memory: 4GB  
  
-   Minimum hard disk space: 2GB  
  
-   TCP\/IP connectivity must be enabled. \(See [Enable or Disable a Server Network Protocol](../../Topics\TopicNameContainA/Enable-or-Disable-a-Server-Network-Protocol.md).\)  
  
 An external data source, one of the following:  
  
-   Hadoop cluster. For supported versions see [Configure PolyBase](#supported).  
  
-   Azure blob storage account.  
  
## Install PolyBase  
 Install PolyBase as part of SQL Server installation. For details, see  [PolyBase installation](../../Topics\TopicNameNotContainA/PolyBase-installation.md).  
  
### How to confirm installation  
 After installation, run the following command to confirm that PolyBase has been successfully installed. If PolyBase is installed, returns 1; otherwise, 0.  
  
```tsql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  
  
##  <a name="supported"></a> Configure PolyBase  
 After installing, you must configure SQL Server to use either your Hadoop version, or Azure Blob storage. PolyBase supports two Hadoop providers, Hortonwork’s Data Platform \(HDP\) and Cloudera’s CDH. You can run Hortonworks on either a Windows or Linux machine, and that is also part of the configuration.  The supported external data sources include:  
  
-   Hortonworks HDP 1.3 on Linux\/Windows Server  
  
-   Hortonworks HDP 2.0 – 2.3 on Linux\/Windows Server  
  
-   Cloudera CDH 4.3 on Linux  
  
-   Cloudera CDH 5.1 – 5.5 on Linux  
  
-   Azure blob storage  
  
### External data source configuration  
  
1.  Run [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md) ‘hadoop connectivity’ and set an appropriate value.  To find the value, see [PolyBase Connectivity Configuration &#40;Transact-SQL&#41;](../Topic/PolyBase%20Connectivity%20Configuration%20\(Transact-SQL\).md).  
  
    ```tsql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  You must restart  SQL Server using **services.msc**. Restarting SQL Server restarts these services:  
  
    -   SQL Server PolyBase Data Movement Service  
  
    -   SQL Server PolyBase Engine  
  
 ![stop and start PolyBase services in services.msc](../../Images\Image\ImageNotContaina/polybase-stop-start.png "polybase-stop-start")  
  
### Pushdown configuration  
 To improve query performance,  enable pushdown computation to a Hadoop cluster:  
  
1.  Find the file **yarn\-site.xml** in the installation path of SQL Server. Typically, the path is:  
  
    ```  
  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf\  
  
    ```  
  
2.  On the Hadoop machine, find the analogous file in the Hadoop configuration directory. In the file, find and copy the value of the configuration key yarn.application.classpath.  
  
3.  On the SQL Server machine, in the **yarn.site.xml file,** find the **yarn.application.classpath** property. Paste the value from the Hadoop machine into the value element.  
  
## Scale out PolyBase  
 The PolyBase group feature allows you to create a cluster of SQL Server instances to process large data sets from external data sources  in a scale\-out fashion for better query performance.  
  
1.  Install SQL Server with PolyBase on multiple machines.  
  
2.  Select one SQL Server as head node.  
  
3.  Add other instances as compute nodes by running [sp_polybase_join_group](../Topic/sp_polybase_join_group.md).  
  
    ```  
    -- Enter head node details:   
    -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';  
  
    ```  
  
4.  Restart the PolyBase Data Movement Service on the compute nodes.  
  
 For details, see [PolyBase scale-out groups](../../Topics\TopicNameNotContainA/PolyBase-scale-out-groups.md).  
  
## Create T\-SQL objects  
 Create objects depending on the external data source, either Hadoop or Azure storage.  
  
### Hadoop  
  
```sql  
-- 1: Create a database scoped credential.  
-- Create a master key on the database. This is required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- 2: Create a database scoped credential  for Kerberos-secured Hadoop clusters.  
-- IDENTITY: the Kerberos user name.  
-- SECRET: the Kerberos password  
  
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1   
WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
  
-- 3:  Create an external data source.  
-- LOCATION (Required) : Hadoop Name Node IP address and port.  
-- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
-- CREDENTIAL (Optional):  the database scoped credential, created above.  
  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
        TYPE = HADOOP,   
        LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',   
        RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',   
        CREDENTIAL = HadoopUser1        
);  
  
-- 4: Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
-- 5:  Create an external table pointing to data stored in Hadoop.  
-- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = MyHadoopCluster,  
        FILE_FORMAT = TextFileFormat  
);  
  
-- 6:  Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
### Azure blob storage  
  
```sql  
--1: Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Azure blob storage.  
-- IDENTITY: any string (this is not used for authentication to Azure storage).  
-- SECRET: your Azure storage account key.  
  
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential   
WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';  
  
--2:  Create an external data source.  
-- LOCATION:  Azure account storage account name and blob container name.  
-- CREDENTIAL: The database scoped credential created above.  
  
CREATE EXTERNAL DATA SOURCE AzureStorage with (  
        TYPE = HADOOP,   
        LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
        CREDENTIAL = AzureStorageCredential  
);  
  
--3:  Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
--4: Create an external table.  
-- The external table points to data stored in Azure storage.  
-- LOCATION: path to a file or directory that contains the data (relative to the blob container).  
-- To point to all files under the blob container, use LOCATION='/'   
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = AzureStorage,  
        FILE_FORMAT = TextFileFormat  
);  
  
--5: Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## PolyBase queries  
 There are three functions that PolyBase is suited for:  
  
-   ad\-hoc queries against external tables.  
  
-   importing data.  
  
-   exporting data.  
  
### Query examples  
  
-   Ad\-hoc queries  
  
    ```tsql  
    -- PolyBase Scenario 1: Ad-Hoc Query joining relational with Hadoop data   
    -- Select customers who drive faster than 35 mph: joining structured customer data stored   
    -- in SQL Server with car sensor data stored in Hadoop.  
    SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,   
            Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
    FROM Insured_Customers, CarSensor_Data  
    WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35   
    ORDER BY CarSensor_Data.Speed DESC  
    OPTION (FORCE EXTERNALPUSHDOWN);	-- or OPTION (DISABLE EXTERNALPUSHDOWN)  
    ```  
  
-   Importing data  
  
    ```tsql  
    -- PolyBase Scenario 2: Import external data into SQL Server.  
    -- Import data for fast drivers into SQL Server to do more in-depth analysis and  
    -- leverage Columnstore technology.  
  
    SELECT DISTINCT   
            Insured_Customers.FirstName, Insured_Customers.LastName,   
            Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
    INTO Fast_Customers from Insured_Customers INNER JOIN   
    (  
            SELECT * FROM CarSensor_Data where Speed > 35   
    ) AS SensorD  
    ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
    ORDER BY YearlyIncome  
  
    CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
    ```  
  
-   Exporting data  
  
    ```  
    -- PolyBase Scenario 3: Export data from SQL Server to Hadoop.  
  
    -- Enable INSERT into external table  
    sp_configure ‘allow polybase export’, 1;  
    reconfigure  
  
    -- Create an external table.   
    CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
            [FirstName] char(25) NOT NULL,   
            [LastName] char(25) NOT NULL,   
            [YearlyIncome] float NULL,   
            [MaritalStatus] char(1) NOT NULL  
    )  
    WITH (  
            LOCATION='/old_data/2009/customerdata.tbl',  
            DATA_SOURCE = HadoopHDP2,  
            FILE_FORMAT = TextFileFormat,  
            REJECT_TYPE = VALUE,  
            REJECT_VALUE = 0  
    );  
  
    -- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
    INSERT INTO dbo.FastCustomer2009  
    SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
    ON (T1.CustomerKey = T2.CustomerKey)  
    WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
    ```  
  
## Managing PolyBase objects in SSMS  
 In SSMS, external tables are displayed in a separate folder **External Tables**. External data sources and external file formats are in subfolders under **External Resources**.  
  
 ![PolyBase objects in SSMS](../../Images\Image\ImageNotContaina/polybase_management.png "polybase_management")  
  
## Troubleshooting  
 Use DMVs to troubleshoot performance and queries. For details, see [PolyBase troubleshooting](../../Topics\TopicNameNotContainA/PolyBase-troubleshooting.md).  
  
 After upgrading from SQL Server 2016 RC1 to RC2 or RC3, queries may fail. For details and a remedy, see [SQL Server 2016 Release Notes](../../Topics\TopicNameNotContainA/SQL-Server-2016-Release-Notes.md) and search for "PolyBase."  
  
## Next steps  
 To understand the scale\-out feature, see [PolyBase scale-out groups](../../Topics\TopicNameNotContainA/PolyBase-scale-out-groups.md).  To monitor PolyBase, see [PolyBase troubleshooting](../../Topics\TopicNameNotContainA/PolyBase-troubleshooting.md). To trouble shoot PolyBase perfomance, see [PolyBase troubleshooting with dynamic management views](../../Topics\TopicNameNotContainA/PolyBase-troubleshooting-with-dynamic-management-views.md).  
  
## See Also  
 [PolyBase Guide](../../Topics\TopicNameNotContainA/PolyBase-Guide.md)   
 [PolyBase scale-out groups](../../Topics\TopicNameNotContainA/PolyBase-scale-out-groups.md)   
 [PolyBase stored procedures](../Topic/PolyBase%20stored%20procedures.md)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../Topic/CREATE%20EXTERNAL%20DATA%20SOURCE%20\(Transact-SQL\).md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../Topic/CREATE%20EXTERNAL%20FILE%20FORMAT%20\(Transact-SQL\).md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../Topic/CREATE%20EXTERNAL%20TABLE%20\(Transact-SQL\).md)  
  
  