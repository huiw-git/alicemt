---
title: "Data Sources in Multidimensional Models"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
caps.latest.revision: 46
caps.handback.revision: 0
manager: mblythe
---
# Data Sources in Multidimensional Models
All data that you import or load into a multidimensional model originates from an external data source. Typically, source data is from a data warehouse designed for reporting purposes, but it could come from any relational database that is accessed directly or indirectly through an intermediary, such as an [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] package.  
  
 A **data source** object in [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] specifies a direct connection to an external data source. In addition to physical location, a data source object specifies the connection string, data provider, credentials, and other properties that control connection behavior.  
  
 Information provided by the data source object is used during the following operations:  
  
-   Get schema information and other metadata used to generate data source views into a model.  
  
-   Query or load data into a model during processing.  
  
-   Run queries against multidimensional or data mining models that use ROLAP storage mode.  
  
-   Read or write to remote partitions.  
  
-   Connect to linked objects, as well as synchronize from target to source.  
  
-   Perform write back operations that update fact table data stored in a relational database.  
  
 When building a multidimensional model from the bottom up, you start by creating the data source object, and then use it to generate the next object, a **data source view**. A data source view is the data abstraction layer in the model. It is typically created after the data source object, using the schema of the source database as the basis. However, you can choose other ways to build a model, including starting with cubes and dimensions, and generating the schema that best supports your design.  
  
 Regardless of how you build it, each model requires at least one data source object that specifies a connection to source data. You can create multiple data source objects in a single model to use data from different sources or vary connection properties for specific objects.  
  
 Data source objects can be managed independently of other objects in your model. After you create a data source, you can change its properties later, and then preprocess the model to ensure the data is retrieved correctly.  
  
## Related Topics and Tasks  
  
|Topic|Description|  
|-----------|-----------------|  
|[Supported Data Sources (SSAS - Multidimensional)](../../Topics/TopicNameNotContainA/Supported-Data-Sources--SSAS---Multidimensional-.md)|Describes the types of data sources that can be used in a multidimensional model.|  
|[Create a Data Source (SSAS Multidimensional)](../../Topics/TopicNameContainA/Create-a-Data-Source--SSAS-Multidimensional-.md)|Explains how to add a data source object to a multidimensional model.|  
|[Delete a Data Source in Solution Explorer (SSAS Multidimensional)](../../Topics/TopicNameContainA/Delete-a-Data-Source-in-Solution-Explorer--SSAS-Multidimensional-.md)|Use this procedure to delete a data source object from a multidimensional model.|  
|[Set Data Source Properties (SSAS Multidimensional)](../../Topics/TopicNameNotContainA/Set-Data-Source-Properties--SSAS-Multidimensional-.md)|Describes each property and explains how to set each one.|  
|[Set Impersonation Options (SSAS - Multidimensional)](../../Topics/TopicNameNotContainA/Set-Impersonation-Options--SSAS---Multidimensional-.md)|Explains how to configure options in the Impersonation Information dialog box.|  
  
## See Also  
 [Analysis Services Objects](assetId:///f76d869b-fc1d-4807-9f28-da09c7be382d)   
 [Logical Architecture (Analysis Services - Multidimensional Data)](assetId:///1b9cae0a-8990-4194-af5f-a1ea5f2aff06)   
 [Data Source Views in Multidimensional Models](../../Topics/TopicNameNotContainA/Data-Source-Views-in-Multidimensional-Models.md)   
 [Data Sources and Bindings (SSAS Multidimensional)](../../Topics/TopicNameNotContainA/Data-Sources-and-Bindings--SSAS-Multidimensional-.md)