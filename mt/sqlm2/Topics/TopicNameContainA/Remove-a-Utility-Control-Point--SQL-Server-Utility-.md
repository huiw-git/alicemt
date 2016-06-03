---
title: Remove a Utility Control Point (SQL Server Utility)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
---
# Remove a Utility Control Point (SQL Server Utility)
  This topic describes how to remove a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] utility control point \(UCP\) from the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To remove a Utility Control Point, using:**  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 Before you use this procedure to remove the UCP from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility, note the following requirements. The stored procedure will run prerequisite checks as part of the operation.  
  
-   Before you run this procedure, all managed instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be removed from the UCP. Note that the UCP is a managed instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. From more information, see [Remove an Instance of SQL Server from the SQL Server Utility](../../Topics\TopicNameNotContainA/Remove-an-Instance-of-SQL-Server-from-the-SQL-Server-Utility.md).  
  
-   This procedure must be run on a computer that is a UCP.  
  
-   If the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] where the UCP was removed has a non\-Utility data collection set, the UMDW database \(sysutility\_mdw\) will not be dropped by the procedure. If this is the case, the UMDW database \(sysutility\_mdw\) must be dropped manually before the UCP can be created again.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 This procedure must be run by a user with **sysadmin** permissions; the same permissions required to create a UCP.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To remove a Utility Control Point  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## See Also  
 [SQL Server Utility Features and Tasks](../../Topics\TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md)   
 [Use Utility Explorer to Manage the SQL Server Utility](../../Topics\TopicNameNotContainA/Use-Utility-Explorer-to-Manage-the-SQL-Server-Utility.md)   
 [Troubleshoot the SQL Server Utility](../../Topics\TopicNameNotContainA/Troubleshoot-the-SQL-Server-Utility.md)  
  
  