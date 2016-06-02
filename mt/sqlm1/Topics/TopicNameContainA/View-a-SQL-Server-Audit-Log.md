---
title: View a SQL Server Audit Log
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
---
# View a SQL Server Audit Log
  This topic describes how to view a SQL Server audit log in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view a SQL Server audit log, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires the **CONTROL SERVER** permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view a SQL Server audit log  
  
1.  In Object Explorer, expand the **Security** folder.  
  
2.  Expand the **Audits** folder.  
  
3.  Right\-click the audit log that you want to view and select **View Audit Logs**. This opens the **Log File Viewer –***server\_name* dialog box. For more information, see [Log File Viewer F1 Help](../../Topics\TopicNameNotContainA/Log-File-Viewer-F1-Help.md).  
  
4.  When finished, click **Close**.  
  
 [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends viewing the audit log by using the Log File Viewer. However, if you are creating an automated monitoring system, the information in the audit file can be read directly by using the [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../Topic/sys.fn_get_audit_file%20\(Transact-SQL\).md) function. Reading the file directly returns data in a slightly different \(unprocessed\) format. See **sys.fn\_get\_audit\_file** for more information.  
  
## See Also  
 [SQL Server Audit &#40;Database Engine&#41;](../Topic/SQL%20Server%20Audit%20\(Database%20Engine\).md)   
 [Write SQL Server Audit Events to the Security Log](../../Topics\TopicNameNotContainA/Write-SQL-Server-Audit-Events-to-the-Security-Log.md)  
  
  