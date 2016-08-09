---
title: "Load or Update Members (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcd7332e-2a60-4e27-a760-383e8ebb23a2
caps.latest.revision: 9
manager: jhubbard
robots: noindex,nofollow
---
# Load or Update Members (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], you can use the staging process to create, update, and delete members in bulk. You can also use the staging process to set and update attribute values.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to insert data into the stg.name_Leaf (for leaf members) or the stg.name_Consolidated (for consolidated members) table in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
-   You must have permissions to execute either the stg.udp_name_Leaf (for leaf members) or stg.udp_name_Consolidated (for consolidated members) stored procedure in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
-   The model must not have a status of **Committed**.  
  
### To load members into the MDS database  
  
1.  Prepare the members for import into the appropriate staging table in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
    -   For leaf members, use stg.name_Leaf. For more information about the required fields, see [Leaf Member Staging Table (Master Data Services)](../../Topics/TopicNameNotContainA/Leaf-Member-Staging-Table--Master-Data-Services-.md).  
  
    -   For consolidated members, use stg.name_Consolidated. For more information about the required fields, see [Consolidated Member Staging Table (Master Data Services)](../../Topics/TopicNameNotContainA/Consolidated-Member-Staging-Table--Master-Data-Services-.md)  
  
2.  Open [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
3.  Import the data into the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. For information about importing data into a database by using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)], see [Start the SQL Server Import and Export Wizard](../../Topics/TopicNameNotContainA/Start-the-SQL-Server-Import-and-Export-Wizard.md).  
  
4.  After you successfully import the data, run the stored procedure to load the staged data into the appropriate tables in the MDS database. For more information on the stored procedure, see [Staging Stored Procedure (Master Data Services)](../../Topics/TopicNameNotContainA/Staging-Stored-Procedure--Master-Data-Services-.md).  
  
## Next Steps  
  
-   View errors that occurred during staging. For more information, see [View Errors that Occur During Staging (Master Data Services)](../../Topics/TopicNameNotContainA/View-Errors-that-Occur-During-Staging--Master-Data-Services-.md).  
  
## See Also  
 [Overview: Importing Data from Tables (Master Data Services)](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)   
 [Staging Process Errors (Master Data Services)](../../Topics/TopicNameNotContainA/Staging-Process-Errors--Master-Data-Services-.md)   
 [Troubleshooting the Staging Process (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)