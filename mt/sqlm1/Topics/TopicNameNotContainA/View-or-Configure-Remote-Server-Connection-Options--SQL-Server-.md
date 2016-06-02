---
title: View or Configure Remote Server Connection Options (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
---
# View or Configure Remote Server Connection Options (SQL Server)
  This topic describes how to view or configure remote server connection options at the server level in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view or configure remote server connection options, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure remote server connection options](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Executing **sp\_serveroption** requires ALTER ANY LINKED SERVER permission on the server.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view or configure remote server connection options  
  
1.  In Object Explorer, right\-click a server, and then click **Properties**.  
  
2.  In the **SQL Server Properties \- \<***server\_name***\>** dialog box, click **Connections**.  
  
3.  On the **Connections** page, review the **Remote server connections** settings, and modify them if necessary.  
  
4.  Repeat steps 1 through 3 on the other server of the remote server pair.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To view remote server connection options  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses [sp\_helpserver](../Topic/sp_helpserver%20\(Transact-SQL\).md) to return information about all remote servers.  
  
```tsql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### To configure remote server connection options  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_serveroption](../Topic/sp_serveroption%20\(Transact-SQL\).md) to configure a remote server. The example configures a remote server corresponding to another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], `SEATTLE3`, to be collation compatible with the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
```tsql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="FollowUp"></a> Follow Up: After you configure remote server connection options  
 The remote server must be stopped and restarted before the setting can take effect.  
  
## See Also  
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [Remote Servers](../../Topics\TopicNameNotContainA/Remote-Servers.md)   
 [Linked Servers &#40;Database Engine&#41;](../Topic/Linked%20Servers%20\(Database%20Engine\).md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../Topic/sp_linkedservers%20\(Transact-SQL\).md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../Topic/sp_helpserver%20\(Transact-SQL\).md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../Topic/sp_serveroption%20\(Transact-SQL\).md)  
  
  