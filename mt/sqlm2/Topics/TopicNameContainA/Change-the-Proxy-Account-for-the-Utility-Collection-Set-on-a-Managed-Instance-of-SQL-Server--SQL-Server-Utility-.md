---
title: Change the Proxy Account for the Utility Collection Set on a Managed Instance of SQL Server (SQL Server Utility)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
---
# Change the Proxy Account for the Utility Collection Set on a Managed Instance of SQL Server (SQL Server Utility)
  This topic describes how to change the proxy account for the Utility Collection Set on a managed instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To change the proxy account for the utility collection set on a managed instance of SQL Server  
  
1.  Remove the managed instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility.  
  
    -   In **Utility Explorer** in SSMS, click on the **Managed Instances** node.  
  
    -   In the **Utility Explorer** list view, right\-click the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance name, and select **Remove Managed Instance…**. For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](../../Topics\TopicNameNotContainA/Remove-an-Instance-of-SQL-Server-from-the-SQL-Server-Utility.md).  
  
2.  Enroll the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility again.  
  
    -   In **Utility Explorer** in SSMS, right\-click on the **Managed Instances** node, and select **Add Managed Instance…**.  
  
    -   Follow prompts to complete the wizard, specifying the new proxy account.  
  
## See Also  
 [SQL Server Utility Features and Tasks](../../Topics\TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md)   
 [Troubleshoot the SQL Server Utility](../../Topics\TopicNameNotContainA/Troubleshoot-the-SQL-Server-Utility.md)  
  
  