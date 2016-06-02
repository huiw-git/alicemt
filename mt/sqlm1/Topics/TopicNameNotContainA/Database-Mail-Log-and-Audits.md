---
title: Database Mail Log and Audits
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
---
# Database Mail Log and Audits
  The Database Mail logging functionality is designed to provide a way to isolate and correct problems. Database Mail stores the log information in the **msdb** database. Information about Database Mail e\-mail content, status of e\-mails, and any messages received, such as errors  are logged by Database Mail and can be used for troubleshooting and auditing purposes.  
  
## Database Mail Logs  
 Tables in the **msdb** database log information from the [Database Mail External Program](../../Topics\TopicNameNotContainA/Database-Mail-External-Program.md). [Database Mail Views &#40;Transact-SQL&#41;](../Topic/Database%20Mail%20Views%20\(Transact-SQL\).md) expose the tables for troubleshooting purposes. Errors appear in the [sysmail_event_log &#40;Transact-SQL&#41;](../Topic/sysmail_event_log%20\(Transact-SQL\).md) view if Service Broker cannot activate the external program, if the external program encounters networking errors or if the Simple Mail Transport Protocol \(SMTP\) server refuses an e\-mail message. In the event that the external program cannot log to the **msdb** tables, the program logs errors to the Windows application event log.  
  
 Internal tables in the **msdb** database contain the e\-mail messages and attachments sent from Database Mail, together with the current status of each message. Database Mail updates these tables as each message is processed.  
  
## Database Mail Auditing tasks  
  
|||  
|-|-|  
|**Reviewing and managing Database Mail logs**|**Link to Topic**|  
|Check the delivery status of an individual message|[Check the Status of E-Mail Messages Sent With Database Mail](../../Topics\TopicNameNotContainA/Check-the-Status-of-E-Mail-Messages-Sent-With-Database-Mail.md)|  
|Clean up Database Mail messages, attachments, and log entries|[sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;](../Topic/sysmail_delete_mailitems_sp%20\(Transact-SQL\).md)<br /><br /> [sysmail_delete_log_sp &#40;Transact-SQL&#41;](../Topic/sysmail_delete_log_sp%20\(Transact-SQL\).md)|  
|Archive the Database Email Messages and Logs|[Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs](../../Topics\TopicNameContainA/Create-a-SQL-Server-Agent-Job-to-Archive-Database-Mail-Messages-and-Event-Logs.md)|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)  
  
  