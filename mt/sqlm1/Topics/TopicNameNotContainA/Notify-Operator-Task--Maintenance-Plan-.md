---
title: Notify Operator Task (Maintenance Plan)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
---
# Notify Operator Task (Maintenance Plan)
  Use the **Notify Operators Task** dialog to add an automatic notification to this maintenance plan. To use this task you must have Database Mail enabled and properly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent operator with a valid e\-mail address.  
  
 This task uses the sp\_notify\_operator stored procedure.  
  
## Options  
 **Connection**  
 Select the server connection to use when performing this task.  
  
 **New**  
 Create a new server connection to use when performing this task. The **New Connection** dialog box is described below.  
  
 **Operators to notify**  
 Specify the recipient of the e\-mail.  
  
 **Notification message subject**  
 Specify the text to include in the notification message subject line.  
  
 **Notification message body**  
 Specify the text to include in the notification message body.  
  
 **View T\-SQL**  
 View the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements performed against the server for this task, based on the selected options.  
  
> [!NOTE]  
>  When the number of objects affected is large, this display can take a considerable amount of time.  
  
## New Connection Dialog Box  
 **Connection name**  
 Enter a name for the new connection.  
  
 **Select or enter a server name**  
 Select a server to connect to when performing this task.  
  
 **Refresh**  
 Refresh the list of available servers.  
  
 **Enter information to log on to the server**  
 Specify how to authenticate against the server.  
  
 **Use Windows integrated security**  
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] with [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Authentication.  
  
 **Use a specific user name and password**  
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. This option is not available.  
  
 **User name**  
 Provide a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login to use when authenticating. This option is not available.  
  
 **Password**  
 Provide a password to use when authenticating. This option is not available.  
  
## See Also  
 [Database Mail](../../Topics\TopicNameNotContainA/Database-Mail.md)   
 [sp_notify_operator &#40;Transact-SQL&#41;](../Topic/sp_notify_operator%20\(Transact-SQL\).md)  
  
  