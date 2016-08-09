---
title: "Connect to Existing Secondary Replicas Page (Add Replica Wizard: Add Databases Wizard)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 850f1bc8-d7d0-425c-bd7b-03f0e9d3348e
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Connect to Existing Secondary Replicas Page (Add Replica Wizard: Add Databases Wizard)
This help topic describes the options of the **Connect to Existing Secondary Replicas** page. This topic is used by the [!INCLUDE[ssAoAddRepWiz](../../Topics/TopicNameNotContainA/tokens/ssAoAddRepWiz_md.md)] and [!INCLUDE[ssAoAddDbWiz](../../Topics/TopicNameNotContainA/tokens/ssAoAddDbWiz_md.md)] of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
 **Grid columns:**  
 **Server Instance**  
 Displays the name of the server instance that will host the availability replica.  
  
 **Connected As**  
 Displays the account that is connected to the server instance, once the connection has been established. If this column displays "**Not Connected**" for a given server instance, you will need to click either the **Connect** or **Connect All** button.  
  
 **Connect**  
 Click if this server instance is running under a different account than other server instances to which you need to connect.  
  
 **Connect All**  
 Click only if every instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to which you need to connect is running as a service in the same user account.  
  
 **Cancel**  
 Click to cancel the wizard. On the **Connect to Existing Secondary Replica** page, cancelling the wizard cause it to exit without performing any actions.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Use the Add Replica to Availability Group Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Add-Replica-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md)  
  
-   [Use the Add Database to Availability Group Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Add-Database-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md)  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)