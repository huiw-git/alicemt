---
title: "PolyBase T-SQL objects"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-03-08
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-polybase
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef5d6c40-6ce6-4cf0-8ad3-38f98b32f98e
caps.latest.revision: 19
manager: jhubbard
---
# PolyBase T-SQL objects
To use  PolyBase, you must create external tables to reference your external data.  
  
 [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045)  
  
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](assetId:///75d8a220-0f4d-4d91-8ba4-9d852b945509)  
  
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](assetId:///abd5ec8c-1a0e-4d38-a374-8ce3401bc60c)  
  
 [CREATE EXTERNAL TABLE (Transact-SQL)](assetId:///6a6fd8fe-73f5-4639-9908-2279031abdec)  
  
 [CREATE STATISTICS (Transact-SQL)](assetId:///b23e2f6b-076c-4e6d-9281-764bdb616ad2)  
  
## Prerequisites  
 Configure PolyBase. See [PolyBase configuration](../../Topics/TopicNameNotContainA/PolyBase-configuration.md).  
  
## Create external tables for Hadoop  
 **1. Create Database Scoped Credential**  
  
 This step is required only for Kerberos-secured Hadoop clusters.  
  
```sql  
-- Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Kerberos-secured Hadoop clusters.  
-- IDENTITY: the Kerberos user name.  
-- SECRET: the Kerberos password  
  
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1   
WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
  
```  
  
 **2. Create External Data Source**  
  
```sql  
-- Create an external data source.  
-- LOCATION (Required) : Hadoop Name Node IP address and port.  
-- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
-- CREDENTIAL (Optional):  the database scoped credential, created above.  
  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
        TYPE = HADOOP,   
        LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',   
        RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',   
        CREDENTIAL = HadoopUser1 	  
);  
  
```  
  
 **3. Create External File Format**  
  
```sql  
-- Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
```  
  
 **4. Create External Table**  
  
```sql  
-- Create an external table pointing to data stored in Hadoop.  
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
  
```  
  
 **5. Create Statistics**  
  
```sql  
-- Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## Create external tables for Azure blob storage  
 **1. Create Database Scoped Credential**  
  
```sql  
-- Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Azure blob storage.  
-- IDENTITY: any string (this is not used for authentication to Azure storage).  
-- SECRET: your Azure storage account key.  
  
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential   
WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';  
  
```  
  
 **2. Create External Data Source**  
  
```sql  
-- Create an external data source.  
-- LOCATION:  Azure account storage account name and blob container name.  
-- CREDENTIAL: The database scoped credential created above.  
  
CREATE EXTERNAL DATA SOURCE AzureStorage with (  
        TYPE = HADOOP,   
        LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
        CREDENTIAL = AzureStorageCredential  
);  
  
```  
  
 **3. Create External File Format**  
  
```sql  
-- Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
```  
  
 **4. Create External Table**  
  
```sql  
-- Create an external table pointing to data stored in Azure storage.  
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
  
```  
  
 **5. Create Statistics**  
  
```sql  
-- Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## Next steps  
 For examples of queries, see [PolyBase Queries](../../Topics/TopicNameNotContainA/PolyBase-Queries.md).  
  
## See Also  
 [Get started with PolyBase](../../Topics/TopicNameNotContainA/Get-started-with-PolyBase.md)   
 [PolyBase Guide](../../Topics/TopicNameNotContainA/PolyBase-Guide.md)