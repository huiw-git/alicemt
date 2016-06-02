---
title: Move Explicit Hierarchy Members (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5361219-b1cc-453f-9bd2-8a6b0a96a3d9
robots: noindex,nofollow
---
# Move Explicit Hierarchy Members (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], you can use the staging process to move the location of members in explicit hierarchies in bulk. You can designate:  
  
-   A consolidated member as a parent of a consolidated member.  
  
-   A consolidated member as a parent of a leaf member.  
  
-   A leaf member as a sibling of a leaf or consolidated member.  
  
-   A consolidated member as a sibling of a leaf or consolidated member.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to insert data into the stg.name\_Relationship table in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
-   You must have permission to execute the stg.udp\_name\_Relationship stored procedure in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
-   The model must not have a status of **Committed**.  
  
### To move explicit hierarchy members  
  
1.  Prepare the members for import into the stg.name\_Relationship table in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. For more information about the required fields, see [Relationship Staging Table &#40;Master Data Services&#41;](../Topic/Relationship%20Staging%20Table%20\(Master%20Data%20Services\).md).  
  
2.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
3.  Import the data into stg.name\_Relationship. For information about importing data into a database by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
4.  After you successfully import the data, run the stg.udp\_name\_Relationship stored procedure to load the staged data into the appropriate MDS tables. For more information about the stored procedure, see [Staging Stored Procedure &#40;Master Data Services&#41;](../Topic/Staging%20Stored%20Procedure%20\(Master%20Data%20Services\).md)  
  
## Next Steps  
  
-   View errors that occurred during staging. For more information, see [View Errors that Occur During Staging &#40;Master Data Services&#41;](../Topic/View%20Errors%20that%20Occur%20During%20Staging%20\(Master%20Data%20Services\).md).  
  
## See Also  
 [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)   
 [Move Members within a Hierarchy &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)   
 [Staging Process Errors &#40;Master Data Services&#41;](../Topic/Staging%20Process%20Errors%20\(Master%20Data%20Services\).md)   
 [Troubleshooting the Staging Process \(Master Data Services\)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  