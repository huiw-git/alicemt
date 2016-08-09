---
title: "Move Explicit Hierarchy Members (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5361219-b1cc-453f-9bd2-8a6b0a96a3d9
caps.latest.revision: 8
manager: jhubbard
robots: noindex,nofollow
---
# Move Explicit Hierarchy Members (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], you can use the staging process to move the location of members in explicit hierarchies in bulk. You can designate:  
  
-   A consolidated member as a parent of a consolidated member.  
  
-   A consolidated member as a parent of a leaf member.  
  
-   A leaf member as a sibling of a leaf or consolidated member.  
  
-   A consolidated member as a sibling of a leaf or consolidated member.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to insert data into the stg.name_Relationship table in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
-   You must have permission to execute the stg.udp_name_Relationship stored procedure in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
-   The model must not have a status of **Committed**.  
  
### To move explicit hierarchy members  
  
1.  Prepare the members for import into the stg.name_Relationship table in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. For more information about the required fields, see [Relationship Staging Table (Master Data Services)](../../Topics/TopicNameNotContainA/Relationship-Staging-Table--Master-Data-Services-.md).  
  
2.  Open [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
3.  Import the data into stg.name_Relationship. For information about importing data into a database by using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)], see [Start the SQL Server Import and Export Wizard](../../Topics/TopicNameNotContainA/Start-the-SQL-Server-Import-and-Export-Wizard.md).  
  
4.  After you successfully import the data, run the stg.udp_name_Relationship stored procedure to load the staged data into the appropriate MDS tables. For more information about the stored procedure, see [Staging Stored Procedure (Master Data Services)](../../Topics/TopicNameNotContainA/Staging-Stored-Procedure--Master-Data-Services-.md)  
  
## Next Steps  
  
-   View errors that occurred during staging. For more information, see [View Errors that Occur During Staging (Master Data Services)](../../Topics/TopicNameNotContainA/View-Errors-that-Occur-During-Staging--Master-Data-Services-.md).  
  
## See Also  
 [Overview: Importing Data from Tables (Master Data Services)](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)   
 [How to: Move Members in a Hierarchy (Master Data Services)](assetId:///049c9a15-89c1-478c-8438-028fffc9e187)   
 [Staging Process Errors (Master Data Services)](../../Topics/TopicNameNotContainA/Staging-Process-Errors--Master-Data-Services-.md)   
 [Troubleshooting the Staging Process (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)