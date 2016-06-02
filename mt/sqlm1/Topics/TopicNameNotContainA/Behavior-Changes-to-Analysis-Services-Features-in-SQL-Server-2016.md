---
title: Behavior Changes to Analysis Services Features in SQL Server 2016
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
---
# Behavior Changes to Analysis Services Features in SQL Server 2016
  A *behavior change* affects how features work or interact in the current version as compared to earlier versions of SQL Server.  
  
 Revisions to  default values, manual configuration required to complete an upgrade or restore functionality, or a new implementation of an existing feature are all examples of a behavior change in the product.  
  
 Feature behaviors that changed in this release, yet do not break an existing model or code post\-upgrade, are listed here.  
  
> [!NOTE]  
>  In contrast with a *behavior change*, a *breaking change* is one that prevents a data model or application integrated with [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] from running after upgrading a server, client tool, or model. To see the list, visit [Breaking Changes to Analysis Services Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Breaking-Changes-to-Analysis-Services-Features-in-SQL-Server-2016.md).  
  
## Analysis Services in SharePoint mode  
 Running the Power Pivot Configuration wizard is no longer required as a post\-installation task. This is true for all supported versions of SharePoint that load models from the  current [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] release of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].  
  
## DirectQuery mode for Tabular models  
 *DirectQuery* is a data access mode for tabular models, where query execution is performed on a backend relational database, retrieving a result set in real time. It's often used for very large datasets that cannot fit in memory or when data is volatile and you want the most recent data returned in queries against a tabular model.  
  
 DirectQuery has existed as a data access mode for the last several releases. In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], the implementation has been slightly revised, assuming the tabular model is at compatibility level 1200. DirectQuery has fewer restrictions than before. It also has different database properties.  
  
 If you are using DirectQuery in an existing tabular model, you can keep the model at its currently compatibility level of 1100 or 1103 and continue to use DirectQuery as its implemented for those levels. Alternatively, you can upgrade to 1200 to benefit from enhancements made to DirectQuery in this release of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].  
  
 There is no in\-place upgrade of a DirectQuery model because the settings from older compatibility levels do not have exact counterparts in the newer 1200 compatibility level. If you have an existing tabular model that runs in DirectQuery mode, you should open the model in SQL Server Data Tools, turn DirectQuery off, set the **Compatibility Level** property to 1200, and then reconfigure the DirectQuery properties as defined for tabular 1200 models. See [DirectQuery Mode &#40;SSAS Tabular&#41;](../Topic/DirectQuery%20Mode%20\(SSAS%20Tabular\).md) for details.  
  
## See Also  
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)   
 [Breaking Changes to Analysis Services Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Breaking-Changes-to-Analysis-Services-Features-in-SQL-Server-2016.md)   
 [Compatibility Level for Tabular models in Analysis Services](../../Topics\TopicNameNotContainA/Compatibility-Level-for-Tabular-models-in-Analysis-Services.md)   
 [Download SQL Server Data Tools](https://msdn.microsoft.com/en-us/library/mt204009.aspx)  
  
  