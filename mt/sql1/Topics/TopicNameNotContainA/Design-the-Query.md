---
title: "Design the Query"
ms.custom: na
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
caps.latest.revision: 42
caps.handback.revision: 0
manager: mblythe
---
# Design the Query
Use this page of the Report Wizard to create a query by typing the query manually, by using Query Builder to interactively build a query, or by importing a query from another report.  
  
 The data source type you chose on the Select the Data Source page, a previous page in the Report Wizard, determines the query you can enter on this page. For example, if the data source type is [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], you can enter [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements or stored procedure names. If the data source type is [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], the Query pane is disabled and you cannot enter a query directly. You can specify the query by using Query Builder.  
  
## Options  
 **Query string**  
 Type a query that retrieves the data you want to use in your report.  
  
 **Query Builder**  
 Click **Query Builder** to open a query designer for the data source, or to import a query from another report.  
  
 For more information about query designers, see [Reporting Services Query Designers](../../Topics/TopicNameNotContainA/Reporting-Services-Query-Designers.md).  
  
## Example  
 For the data source type **Microsoft SQL Server**, the following query retrieves a list of last names from the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database **Person** table.  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 For the data source type **Microsoft SQL Server**, the following query runs the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] stored procedure **uspGetEmployeeManagers** for the employee with identification number 1:  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## See Also  
 [Report Wizard Help](../../Topics/TopicNameNotContainA/Report-Wizard-Help.md)   
 [Report Embedded Datasets and Shared Datasets (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Report-Embedded-Datasets-and-Shared-Datasets--Report-Builder-and-SSRS-.md)   
 [Report Datasets (SSRS)](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md)