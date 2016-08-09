---
title: "Considerations for Running Utility and non-Utility Collection Sets on the Same Instance of SQL Server"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Considerations for Running Utility and non-Utility Collection Sets on the Same Instance of SQL Server
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility collection set is supported side-by-side with non- [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility collection sets. That is, a managed instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can be monitored by other collection sets while it is a member of a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility. However, you must disable non- [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility data collection functionality while the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is being enrolled into the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility.  
  
 After the instance is enrolled with the UCP, you can restart non- [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility collection sets. Note, however, that all collection sets on the managed instance will upload their data to the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.  
  
 To run [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility collection sets side-by-side with non- [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility collection sets, consider the following points:  
  
-   Side-by-side collection sets are supported.  
  
-   You must disable existing data collectors while enrolling instances into the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility.  
  
-   To pass validation requirements, you must run the following stored procedures on the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] before you create a UCP, and on an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] before you enroll it into the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility:  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     If you do not run these stored procedures before you launch the Create UCP Wizard or Add Managed Instance Wizard, the operation will fail.  
  
-   You must use the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Utility UMDW (sysutility_mdw) for all collection sets on a managed instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
## See Also  
 [SQL Server Utility Features and Tasks](../../Topics/TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md)   
 [Configure Your Utility Control Point Data Warehouse (SQL Server Utility)](../../Topics/TopicNameNotContainA/Configure-Your-Utility-Control-Point-Data-Warehouse--SQL-Server-Utility-.md)