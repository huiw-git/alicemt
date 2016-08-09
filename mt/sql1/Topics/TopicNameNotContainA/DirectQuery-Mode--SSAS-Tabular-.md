---
title: "DirectQuery Mode (SSAS Tabular)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45ad2965-05ec-4fb1-a164-d8060b562ea5
caps.latest.revision: 60
caps.handback.revision: 0
manager: mblythe
---
# DirectQuery Mode (SSAS Tabular)
Analysis Services lets you access data from a Tabular model by retrieving data and aggregates directly from a relational database system in *DirectQuery mode*. You can configure DirectQuery using Management Studio for a deployed database, or in SQL Server Data Tools (SSDT) when designing the model.  
  
 To switch to DirectQuery mode, select **model.bim** in Solution Explorer in [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)], and then set DirectQuery mode to **On**. For more information, see [Enable DirectQuery mode in SSDT](../../Topics/TopicNameNotContainA/Enable-DirectQuery-mode-in-SSDT.md).  
  
> [!NOTE]  
>  How you work with DirectQuery will vary depending on the compatibility mode of the model. For the new 1200 compatibility level introduced in SQL Server 2016, you have more control over data in design mode, with the ability to use no data, a sample data set (based on a user-defined query), or full data. Older compatibility level models at 1100 or 1103 use the DirectQuery mode from previous versions of Analysis Services. See [DirectQuery for Tabular 1100 or 1103 models (SSAS Tabular)](../../Topics/TopicNameNotContainA/DirectQuery-for-Tabular-1100-or-1103-models--SSAS-Tabular-.md) if you're supporting older models.  
>   
>  You can determine the compatibility level of model by looking at the model properties list. To upgrade a model to 1200 compatibility level in SQL Server Data Tools, temporarily turn off DirectQuery mode and then change the model's **CompatibilityLevel** property. Remember that upgrade is irreversible so be sure to backup your model first. See [Upgrade Analysis Services](../../Topics/TopicNameNotContainA/Upgrade-Analysis-Services.md) for more information.  
  
##  <a name="bkmk_Benefits"></a> Benefits of DirectQuery Mode  
 By default, Tabular models use an in-memory cache to store and query data. When Tabular models use data that resides in memory, even complex queries can be incredibly fast. However, there are some drawbacks to using cached data. Namely, large data sets can exceed available memory, and data freshness requirements can be difficult if not impossible to achieve on a regular processing schedule.  
  
 DirectQuery overcomes these limitations while also leveraging RDBMS features that can make query execution more efficient. With DirectQuery:  
  
-   Data is guaranteed to be up-to-date, and there is no extra management overhead of having to maintain a separate copy of the data. Changes to the underlying source data can be immediately reflected in queries against the data model.  
  
-   Data sets can be larger than the memory capacity of an Analysis Services server.  
  
-   DirectQuery can take advantage of provider-side query acceleration, such as that provided by xVelocity memory optimized column indexes.  
  
-   Security can be enforced by the back-end database , using row-level security features from the database (alternatively, you can use row-level security in the model via DAX).  
  
-   If the model contains complex formulas that might require multiple queries, Analysis Services can perform optimization to ensure that the query plan for the query executed against the back-end database will be as efficient as possible.  
  
##  <a name="bkmk_prereq"></a> Feature limitations in  DirectQuery mode  
 DirectQuery is significantly improved in this release, but still has a few restrictions. Before switching modes, determine whether the advantages of query execution on the backend server outweigh any reduction in functionality when data processing is offloaded to an external RDBMS.  
  
 If you change the mode of an existing model in [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)], the model designer will notify you of any features in your model that are incompatible with DirectQuery mode.  
  
 The following list summarizes the main feature limitations to keep in mind:  
  
|||  
|-|-|  
|**Feature area**|**Limitation**|  
|**Data sources**|DirectQuery models can only use data from a single relational database of the following types: SQL Server, Oracle, Teradata.  See [Data Sources Supported (SSAS Tabular)](../../Topics/TopicNameNotContainA/Data-Sources-Supported--SSAS-Tabular-.md) for version information.|  
|**Calculated tables**|Calculated tables are not supported in DirectQuery models, but calculated columns are. If you try to convert a tabular model that contains a calculated table, an error will occur stating that the model cannot contain pasted data.|  
|**DAX limitations**|[!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] converts all DAX formulas and measure definitions into SQL statements when querying a DirectQuery model. Any formula containing elements that cannot be converted into SQL syntax will trigger validation errors on the model.<br /><br /> This restriction is mostly limited to functions. For measures, DAX formulas are converted to set-based operations against the relational data store. This means that all measures created implicitly are supported.<br /><br /> Functions that are not supported or that behave inconsistently across platforms include time intelligence functions and statistical functions.<br /><br /> When a validation error occurs, you must substitute a different function, or workaround it by using derived columns in the data source.  Any functions that are off limits will be reported when you switch to DirectQuery mode in the designer. **Note:**  Some formulas in the model might validate when you switch the model to DirectQuery mode, but return different results when executed against the cache vs. the relational data store. This is because calculations against the cache use the semantics of the in-memory analytics (engine, which contains many features meant to emulate the behavior of Excel, whereas queries against data stored in the relational data store necessarily use the semantics of SQL Server.|  
|**Formula consistency**|In certain known cases, the same formula can return different results in a cached or hybrid model compared to a DirectQuery model that uses only the relational data store. These differences are a consequence of the semantic differences between the in-memory analytics engine and SQL Server.<br /><br /> For a complete list of compatibility issues, including functions that might return different results when the model is deployed to real-time, see [DAX Formula Compatibility in DirectQuery Mode (SQL Server Analysis Services)](assetId:///981b6a68-434d-4db6-964e-d92f8eb3ee3e).|  
|**MDX limitations**|No relative object names. All object names must be fully qualified.<br /><br /> No session-scope MDX statements (named sets, calculated members, calculated cells, visual totals, default members, and so forth), but you can use query-scope constructs, such as the 'WITH' clause.<br /><br /> No tuples with members from different levels in MDX subselect clauses.<br /><br /> No user-defined hierarchies.<br /><br /> No native SQL queries (normally, Analysis Services supports a T-SQL subset, but not for DirectQuery models).|  
  
## See Also  
 [Clear the Analysis Services Caches](../../Topics/TopicNameNotContainA/Clear-the-Analysis-Services-Caches.md)   
 [Enable DirectQuery mode in SSMS](../../Topics/TopicNameNotContainA/Enable-DirectQuery-mode-in-SSMS.md)   
 [Partitions (SSAS Tabular)](../../Topics/TopicNameNotContainA/Partitions--SSAS-Tabular-.md)   
 [Tabular Model Projects (SSAS Tabular)](../../Topics/TopicNameNotContainA/Tabular-Model-Projects--SSAS-Tabular-.md)   
 [Analyze in Excel (SSAS Tabular)](../../Topics/TopicNameNotContainA/Analyze-in-Excel--SSAS-Tabular-.md)