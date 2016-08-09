---
title: "Configure the priority boost Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 765f1e83-dd52-44fb-b0c8-1078f213607b
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Configure the priority boost Server Configuration Option
This topic describes how to configure the **priority boost** configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. Use the **priority boost** option to specify whether [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] should run at a higher [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows 2008 or Windows 2008 R2 scheduling priority than other processes on the same computer. If you set this option to 1, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] runs at a priority base of 13 in the Windows 2008 or Windows Server 2008 R2 scheduler. The default is 0, which is a priority base of 7.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureDontUse_md.md)]  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To configure the priority boost option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the priority boost option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Raising the priority too high may drain resources from essential operating system and network functions, resulting in problems shutting down SQL Server or using other operating system tasks on the server.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the priority boost option  
  
1.  In Object Explorer, right-click a server and select **Properties**.  
  
2.  Click the **Processors** node.  
  
3.  Under **Threads**, select the **Boost SQL Server priority** check box.  
  
4.  Stop and restart [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the priority boost option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to set the value of the `priority boost` option to `1`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'priority boost', 1 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the priority boost option  
 The server must be restarted before the setting can take effect.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)