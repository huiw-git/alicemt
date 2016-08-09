---
title: "Database Mail Messaging Objects"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5aa2886e-1db1-4066-85df-57ccf4538c54
caps.latest.revision: 32
caps.handback.revision: 0
manager: jhubbard
---
# Database Mail Messaging Objects
The **msdb** database is the Database Mail host database. This database contains the stored procedures and messaging objects for Database Mail. Microsoft [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] includes the Database Mail Configuration Wizard for enabling Database Mail, creating and managing profiles and accounts, and configuring Database Mail options.  
  
##  <a name="ComponentsAndConcepts"></a> Objects in **msdb** database  
 [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] must be enabled in the **msdb** database. However, Database Mail does not use [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] networking. Therefore, users do not have to create a [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] endpoint to use Database Mail. The external Database Mail process uses a standard [!INCLUDE[vstecado](../../Topics/TopicNameContainA/tokens/vstecado_md.md)] connection to communicate with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 Database Mail exposes the following objects in the **msdb** database when Database Mail is enabled.  
  
 These objects are the interface for Database Mail within the mail host database. Other objects are installed to implement the functionality provided by the objects listed above. However, those objects are reserved for internal use.  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|[sysmail_allitems (Transact-SQL)](assetId:///21fb8432-7677-4435-902f-64a58bba4cbb)|**View**|Lists all messages submitted to Database Mail.|  
|[sysmail_event_log (Transact-SQL)](assetId:///440bc409-1188-4175-afc4-c68e31e44fed)|**View**|Lists messages about the behavior of the [Database Mail External Program](../../Topics/TopicNameNotContainA/Database-Mail-External-Program.md).|  
|[sysmail_faileditems (Transact-SQL)](assetId:///a31562c5-358e-4cfc-a72d-b3faccc53851)|**View**|Information about messages that Database Mail could not sent.|  
|[sysmail_mailattachments (Transact-SQL)](assetId:///aee87059-a4c1-459a-a95c-641b4e3f0e73)|**View**|Information about attachments to Database Mail messages.|  
|[sysmail_sentitems (Transact-SQL)](assetId:///16eb2a44-cebb-4cec-93ac-e2498c39989f)|**View**|Information about messages that have been sent using Database Mail.|  
|[sysmail_unsentitems (Transact-SQL)](assetId:///993c12da-41e5-4e53-a188-0323feb70c67)|**View**|Information about messages that Database Mail in currently trying to send.|  
|[sp_send_dbmail (Transact-SQL)](assetId:///f1d7a795-a3fd-4043-ac4b-c781e76dab47)|**Stored Procedure**|Sends e-mail messages using Database Mail.|  
|[sysmail_delete_log_sp (Transact-SQL)](assetId:///e94b37a1-70ad-46a5-86c0-721892156f7c)|**Stored Procedure**|Deletes messages from the Database Mail log.|  
|[sysmail_delete_mailitems_sp (Transact-SQL)](assetId:///f87c9f4a-bda1-4bce-84b2-a055a3229ecd)|**Stored Procedure**|Deletes mail items from the Database Mail queue.|  
|[sysmail_help_status_sp (Transact-SQL)](assetId:///b44277c6-81e8-4b4d-85b3-a2f04d602e7a)|**Stored Procedure**|Indicates if Database Mail is started.|  
|[sysmail_start_sp (Transact-SQL)](assetId:///25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5)|**Stored Procedure**|Starts the Service Broker objects that the external program uses. These objects are started by default.|  
|[sysmail_stop_sp (Transact-SQL)](assetId:///045ee36f-5bf0-4626-b5ee-e84db06ce16f)|**Stored Procedure**|Stops the Service Broker objects that the external program uses.|  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Database Mail](../../Topics/TopicNameNotContainA/Database-Mail.md)   
 [SQL Server Service Broker](../../Topics/TopicNameNotContainA/SQL-Server-Service-Broker.md)