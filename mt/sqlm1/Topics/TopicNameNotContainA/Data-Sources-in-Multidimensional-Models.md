---
title: Data Sources in Multidimensional Models
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
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
---
# Data Sources in Multidimensional Models
  All data that you import or load into a multidimensional model originates from an external data source. Typically, source data is from a data warehouse designed for reporting purposes, but it could come from any relational database that is accessed directly or indirectly through an intermediary, such as an [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] package.  
  
 A **data source** object in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] specifies a direct connection to an external data source. In addition to physical location, a data source object specifies the connection string, data provider, credentials, and other properties that control connection behavior.  
  
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
|[Supported Data Sources &#40;SSAS - Multidimensional&#41;](../Topic/Supported%20Data%20Sources%20\(SSAS%20-%20Multidimensional\).md)|Describes the types of data sources that can be used in a multidimensional model.|  
|[Create a Data Source &#40;SSAS Multidimensional&#41;](../Topic/Create%20a%20Data%20Source%20\(SSAS%20Multidimensional\).md)|Explains how to add a data source object to a multidimensional model.|  
|[Delete a Data Source in Solution Explorer &#40;SSAS Multidimensional&#41;](../Topic/Delete%20a%20Data%20Source%20in%20Solution%20Explorer%20\(SSAS%20Multidimensional\).md)|Use this procedure to delete a data source object from a multidimensional model.|  
|[Set Data Source Properties &#40;SSAS Multidimensional&#41;](../Topic/Set%20Data%20Source%20Properties%20\(SSAS%20Multidimensional\).md)|Describes each property and explains how to set each one.|  
|[Set Impersonation Options &#40;SSAS - Multidimensional&#41;](../Topic/Set%20Impersonation%20Options%20\(SSAS%20-%20Multidimensional\).md)|Explains how to configure options in the Impersonation Information dialog box.|  
  
## See Also  
 [Database Objects &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Database%20Objects%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Logical%20Architecture%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Data Source Views in Multidimensional Models](../../Topics\TopicNameNotContainA/Data-Source-Views-in-Multidimensional-Models.md)   
 [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](../Topic/Data%20Sources%20and%20Bindings%20\(SSAS%20Multidimensional\).md)  
  
  