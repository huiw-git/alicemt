---
title: "View a SQL Server Audit Log"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# View a SQL Server Audit Log
This topic describes how to view a SQL Server audit log in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
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
  
3.  Right-click the audit log that you want to view and select **View Audit Logs**. This opens the **Log File Viewer –***server_name* dialog box. For more information, see [Log File Viewer F1 Help](../../Topics/TopicNameNotContainA/Log-File-Viewer-F1-Help.md).  
  
4.  When finished, click **Close**.  
  
 [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] recommends viewing the audit log by using the Log File Viewer. However, if you are creating an automated monitoring system, the information in the audit file can be read directly by using the [sys.fn_get_audit_file (Transact-SQL)](assetId:///d6a78d14-bb1f-4987-b7b6-579ddd4167f5) function. Reading the file directly returns data in a slightly different (unprocessed) format. See **sys.fn_get_audit_file** for more information.  
  
## See Also  
 [SQL Server Audit (Database Engine)](../../Topics/TopicNameNotContainA/SQL-Server-Audit--Database-Engine-.md)   
 [Write SQL Server Audit Events to the Security Log](../../Topics/TopicNameNotContainA/Write-SQL-Server-Audit-Events-to-the-Security-Log.md)