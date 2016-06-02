---
title: Working with Policy-Based Management Facets
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
---
# Working with Policy-Based Management Facets
  A Policy\-Based Management facet is a set of logical properties that are related to an area of management interest. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] includes several predefined facets. For example, the Surface Area Configuration facet defines, as properties, the features that are off by default.  
  
 When you manage many similar [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] environments, you can configure a facet in one instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], copy the state of the facet to a file, and then import that file into another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] as a policy. When the state has been converted to a policy, the policy can be applied to other instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], instance objects, databases, or database objects.  
  
 This topic describes how to copy the state of a facet to an XML file.  
  
##  <a name="BeforeYouBegin"></a> Permissions  
 The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.  
  
## Viewing and Copying Facet States  
 [View the Policy-Based Management Facets on a SQL Server Object](../../Topics\TopicNameContainA/View-the-Policy-Based-Management-Facets-on-a-SQL-Server-Object.md)  
  
 [Copy a Policy-Based Management Facet State to an XML File](../../Topics\TopicNameContainA/Copy-a-Policy-Based-Management-Facet-State-to-an-XML-File.md)  
  
## See Also  
 [Administer Servers by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md)  
  
  