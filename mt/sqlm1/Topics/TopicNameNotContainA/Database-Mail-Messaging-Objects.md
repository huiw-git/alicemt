---
title: Database Mail Messaging Objects
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5aa2886e-1db1-4066-85df-57ccf4538c54
---
# Database Mail Messaging Objects
  The **msdb** database is the Database Mail host database. This database contains the stored procedures and messaging objects for Database Mail. Microsoft [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] includes the Database Mail Configuration Wizard for enabling Database Mail, creating and managing profiles and accounts, and configuring Database Mail options.  
  
##  <a name="ComponentsAndConcepts"></a> Objects in **msdb** database  
 [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] must be enabled in the **msdb** database. However, Database Mail does not use [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] networking. Therefore, users do not have to create a [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] endpoint to use Database Mail. The external Database Mail process uses a standard [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection to communicate with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 Database Mail exposes the following objects in the **msdb** database when Database Mail is enabled.  
  
 These objects are the interface for Database Mail within the mail host database. Other objects are installed to implement the functionality provided by the objects listed above. However, those objects are reserved for internal use.  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|[sysmail_allitems &#40;Transact-SQL&#41;](../Topic/sysmail_allitems%20\(Transact-SQL\).md)|**View**|Lists all messages submitted to Database Mail.|  
|[sysmail_event_log &#40;Transact-SQL&#41;](../Topic/sysmail_event_log%20\(Transact-SQL\).md)|**View**|Lists messages about the behavior of the [Database Mail External Program](../../Topics\TopicNameNotContainA/Database-Mail-External-Program.md).|  
|[sysmail_faileditems &#40;Transact-SQL&#41;](../Topic/sysmail_faileditems%20\(Transact-SQL\).md)|**View**|Information about messages that Database Mail could not sent.|  
|[sysmail_mailattachments &#40;Transact-SQL&#41;](../Topic/sysmail_mailattachments%20\(Transact-SQL\).md)|**View**|Information about attachments to Database Mail messages.|  
|[sysmail_sentitems &#40;Transact-SQL&#41;](../Topic/sysmail_sentitems%20\(Transact-SQL\).md)|**View**|Information about messages that have been sent using Database Mail.|  
|[sysmail_unsentitems &#40;Transact-SQL&#41;](../Topic/sysmail_unsentitems%20\(Transact-SQL\).md)|**View**|Information about messages that Database Mail in currently trying to send.|  
|[sp_send_dbmail &#40;Transact-SQL&#41;](../Topic/sp_send_dbmail%20\(Transact-SQL\).md)|**Stored Procedure**|Sends e\-mail messages using Database Mail.|  
|[sysmail_delete_log_sp &#40;Transact-SQL&#41;](../Topic/sysmail_delete_log_sp%20\(Transact-SQL\).md)|**Stored Procedure**|Deletes messages from the Database Mail log.|  
|[sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;](../Topic/sysmail_delete_mailitems_sp%20\(Transact-SQL\).md)|**Stored Procedure**|Deletes mail items from the Database Mail queue.|  
|[sysmail_help_status_sp &#40;Transact-SQL&#41;](../Topic/sysmail_help_status_sp%20\(Transact-SQL\).md)|**Stored Procedure**|Indicates if Database Mail is started.|  
|[sysmail\_start\_sp \(Transact\-SQL\)](../Topic/sysmail_start_sp%20\(Transact-SQL\).md)|**Stored Procedure**|Starts the Service Broker objects that the external program uses. These objects are started by default.|  
|[sysmail\_stop\_sp \(Transact\-SQL\)](../Topic/sysmail_stop_sp%20\(Transact-SQL\).md)|**Stored Procedure**|Stops the Service Broker objects that the external program uses.|  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Database Mail](../../Topics\TopicNameNotContainA/Database-Mail.md)   
 [SQL Server Service Broker](../../Topics\TopicNameNotContainA/SQL-Server-Service-Broker.md)  
  
  