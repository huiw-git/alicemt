---
title: "Database Mail Log and Audits"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Database Mail Log and Audits
The Database Mail logging functionality is designed to provide a way to isolate and correct problems. Database Mail stores the log information in the **msdb** database. Information about Database Mail e-mail content, status of e-mails, and any messages received, such as errors  are logged by Database Mail and can be used for troubleshooting and auditing purposes.  
  
## Database Mail Logs  
 Tables in the **msdb** database log information from the [Database Mail External Program](../../Topics/TopicNameNotContainA/Database-Mail-External-Program.md). [Database Mail Views (Transact-SQL)](assetId:///ab8728e0-803f-4b6f-b66f-9880ec37a49e) expose the tables for troubleshooting purposes. Errors appear in the [sysmail_event_log (Transact-SQL)](assetId:///440bc409-1188-4175-afc4-c68e31e44fed) view if Service Broker cannot activate the external program, if the external program encounters networking errors or if the Simple Mail Transport Protocol (SMTP) server refuses an e-mail message. In the event that the external program cannot log to the **msdb** tables, the program logs errors to the Windows application event log.  
  
 Internal tables in the **msdb** database contain the e-mail messages and attachments sent from Database Mail, together with the current status of each message. Database Mail updates these tables as each message is processed.  
  
## Database Mail Auditing tasks  
  
|||  
|-|-|  
|**Reviewing and managing Database Mail logs**|**Link to Topic**|  
|Check the delivery status of an individual message|[Check the Status of E-Mail Messages Sent With Database Mail](../../Topics/TopicNameNotContainA/Check-the-Status-of-E-Mail-Messages-Sent-With-Database-Mail.md)|  
|Clean up Database Mail messages, attachments, and log entries|[sysmail_delete_mailitems_sp (Transact-SQL)](assetId:///f87c9f4a-bda1-4bce-84b2-a055a3229ecd)<br /><br /> [sysmail_delete_log_sp (Transact-SQL)](assetId:///e94b37a1-70ad-46a5-86c0-721892156f7c)|  
|Archive the Database Email Messages and Logs|[Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs](../../Topics/TopicNameContainA/Create-a-SQL-Server-Agent-Job-to-Archive-Database-Mail-Messages-and-Event-Logs.md)|  
  
## See Also  
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)