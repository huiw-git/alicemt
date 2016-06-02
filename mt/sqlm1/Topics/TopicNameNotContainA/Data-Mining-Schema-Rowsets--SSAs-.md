---
title: Data Mining Schema Rowsets (SSAs)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
---
# Data Mining Schema Rowsets (SSAs)
  In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], many of the existing OLE DB data mining schema rowsets are exposed as a set of system tables that you can query by using Data Mining Extensions \(DMX\) statements. By creating queries against the data mining schema rowset, you can identify the services that are available, get updates on the status of your models and structures, and find out details about the model content or parameters. For a description of the data mining schema rowsets, see [Data Mining Schema Rowsets](../Topic/Data%20Mining%20Schema%20Rowsets.md).  
  
> [!NOTE]  
>  You can also query the data mining schema rowsets by using XMLA. For more information about how to do this in SQL Server Management Studio, see [Create a Data Mining Query by Using XMLA](../../Topics\TopicNameContainA/Create-a-Data-Mining-Query-by-Using-XMLA.md).  
  
## List of Data Mining Schema Rowsets  
 The following table lists the data mining schema rowsets that may be useful for querying and monitoring.  
  
|Rowset name|Description|  
|-----------------|-----------------|  
|DMSCHEMA\_MINING\_MODELS|Lists all mining models in the current context.<br /><br /> Includes such information as the date created, parameters used to create the model, and the size of the training set.|  
|DMSCHEMA\_MINING\_COLUMNS|Lists all columns used in mining models in the current context.<br /><br /> Information includes mapping to mining structure source column, data type, precision, and prediction functions that can be used with the column.|  
|DMSCHEMA\_MINING\_STRUCTURES|Lists all mining structure in the current context.<br /><br /> Information includes whether the structure is populated, the date the structure was last processed, and the definition of the holdout data set for the structure, if any.|  
|DMSCHEMA\_MINING\_STRUCTURE\_COLUMNS|Lists all columns used in mining structures in the current context.<br /><br /> Information includes content type and data type, nullability, and whether the column contains nested table data.|  
|DMSCHEMA\_MINING\_SERVICES|Lists all mining services, or algorithms, that are available on the specified server.<br /><br /> Information includes supported modeling flags, input types, and supported data source types.|  
|DMSCHEMA\_MINING\_SERVICE\_PARAMETERS|Lists all parameters for the mining services that are available on the current instance.<br /><br /> Information includes the data type for each parameter, the default values, and the upper and lower limits.|  
|DMSCHEMA\_MODEL\_CONTENT|Returns the content of the model if the model has been processed.<br /><br /> For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20\(Analysis%20Services%20-%20Data%20Mining\).md).|  
|DBSCHEMA\_CATALOGS|Lists all databases \(catalogs\) in the current instance of Analysis Services.|  
|MDSCHEMA\_INPUT\_DATASOURCES|Lists all data sources in the current instance of Analysis Services.|  
  
> [!NOTE]  
>  The list in the table is not comprehensive; it shows only those rowsets that may be of most interest for troubleshooting.  
  
## Examples  
 The following section provides some examples of queries against the data mining schema rowsets.  
  
### Example 1: List Data Mining Services  
 The following query returns a list of the mining services that are available on the current server, meaning the algorithms that are enabled. The columns provided for each mining service include the modeling flags and content types that can be used by each algorithm, the GUID for each service, and any prediction limits that may have been added for each service.  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### Example 2: List Mining Model Parameters  
 The following example returns the parameters that were used to create a specific mining model:  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### Example 3: List All Rowsets  
 The following example returns a comprehensive list of the rowsets that are available on the current server:  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
  