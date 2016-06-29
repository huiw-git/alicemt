---
title: Enter Passwords Page (Add Replica Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
---
# Enter Passwords Page (Add Replica Wizard)
  This help topic describes the options of the **Enter Passwords** page. This topic applies to the [!INCLUDE[ssAoAddRepWiz](../../Topics/TopicNameNotContainA/includes/ssAoAddRepWiz_md.md)] of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)].  
  
 If the replicas that you selected on the **Specify Replicas** page contain databases that have a database master key, the Enter Passwords page appears.  
  
## Enter Passwords Options  
 The **User databases on this instance of SQL Server** grid lists every local user database. The columns are as follows:  
  
 **Name**  
 Displays the name of a local user database.  
  
 **Size**  
 Displays the database size, if the size is available to the wizard.  
  
 **Status**  
 Indicates **Password required** for databases that have a database master key. After you enter the passwords for the database master keys in the **Passwords** column, click **Refresh**. If you entered the passwords correctly, the **Status** column indicates **Password entered**.  
  
 If the database doesn't have a database master key, the **Status** column indicates **Password not required**.  
  
 **Password**  
 If the **Status** column indicates **Password required**, enter the password for the database master key.  
  
 **Refresh**  
 Click to refresh the grid. This is useful after you enter required passwords.  
  
## Related Tasks  
  
-   [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-Add-Replica-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md)  
  
## See Also  
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Prerequisites--Restrictions--and-Recommendations-for-Always-On-Availability-Groups--SQL-Server-.md)  
  
  