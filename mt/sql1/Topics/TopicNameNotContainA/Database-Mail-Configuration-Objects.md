---
title: "Database Mail Configuration Objects"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03f6e4c0-04ff-490a-bd91-637806215bd1
caps.latest.revision: 34
manager: jhubbard
---
# Database Mail Configuration Objects
Database Mail has two configuration objects: The database configuration objects provide a way for you to configure the settings that Database mail should use when sending an email from your database application or [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent.  
  
-   Database Mail accounts  
  
-   Database Mail profiles  
  
 **In this Topic:**  
  
-   [Database Mail Configuration Object Relationship](#VisualElement)  
  
-   [Database Mail Account](#DBAccount)  
  
-   [Database Mail Profile](#DBProfile)  
  
-   [Database Mail Configuration Tasks](#RelatedTasks)  
  
-   [Additional Database Mail Configuration Tasks (System Stored Procedure)](#Add_Tasks)  
  
-   [Additional References](#RelatedContent)  
  
##  <a name="VisualElement"></a> Database Mail Configuration Object Relationship  
 The illustration shows two profiles, three accounts, and three users. User 1 has access to Profile 1, which uses Account 1 and Account 2. User 3 has access to Profile 2, which uses Account 2 and Account 3. User 2 has access to both Profile 1 and Profile 2.  
  
 ![Relationship of users, profiles, and accounts](../../Topics/TopicNameNotContainA/images/DatabaseMailProfileAccount.gif "DatabaseMailProfileAccount")  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="DBAccount"></a> Database Mail Account  
 A Database Mail account contains the information that Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses to send e-mail messages to an SMTP server. Each account contains information for one e-mail server.  
  
 A Database Mail supports three methods of authentication to communicate with an SMTP server:  
  
-   Windows Authentication: Database Mail uses the credentials of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] Windows service account for authentication on the SMTP server.  
  
-   Basic Authentication:  Database Mail uses the username and password specified to authenticate on the SMTP server.  
  
-   Anonymous Authentication:  The SMTP server does not require any authentication.  Database Mail will not use any credentials to authenticate on the SMTP server.  
  
 Account information is stored in the **msdb** database. Each account consists of the following information:  
  
-   The name of the account.  
  
-   A description of the account.  
  
-   The e-mail address of the account.  
  
-   The display name for the account.  
  
-   The e-mail address to use as the reply-to information for the account.  
  
-   The name of the e-mail server.  
  
-   The type of the e-mail server. For [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], this is always Simple Mail Transfer Protocol(SMTP).  
  
-   The port number of the e-mail server.  
  
-   A bit column indicating whether the connection to the SMTP mail server is made using Secure Sockets Layer (SSL).  
  
-   A bit column indicating whether the connection to the SMTP server is made using the credentials configured for the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)].  
  
-   The user name to use for authentication to the e-mail server, if the e-mail server requires authentication.  
  
-   The password to use for authentication to the e-mail server, if the e-mail server requires authentication.  
  
 The Database Mail Configuration Wizard provides a convenient way to create and manage accounts. You can also use the configuration stored procedures in **msdb** to create and manage accounts.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="DBProfile"></a> Database Mail Profile  
 A Database Mail profile is an ordered collection of related Database Mail accounts. Applications that send e-mail using Database Mail specify profiles, instead of using accounts directly. Separating information about the individual e-mail servers from the objects that the application uses improves flexibility and reliability: profiles provide automatic failover, so that if one e-mail server is unresponsive, Database Mail can automatically send mail to another e-mail server. Database administrators can add, remove, or reconfigure accounts without requiring changes to application code or job steps.  
  
 Profiles also help database administrators control access to e-mail. Membership in the **DatabaseMailUserRole** is required to send Database Mail. Profiles provide additional flexibility for administrators to control who sends mail and which accounts are used.  
  
 A profile may be public or private.  
  
 **Public profiles** are available for all members of the **DatabaseMailUserRole** database role in the **msdb** database. They allow all members of the **DatabaseMailUserRole** role to send e-mail using the profile.  
  
 **Private profiles** are defined for security principals in the **msdb** database. They allow only specified database users, roles, and members of the **sysadmin** fixed server role to send e-mail using the profile. By default, a profile is private, and allows access only to members of the **sysadmin** fixed server role. To use a private profile, **sysadmin** must grant users permission to use the profile. Additionally, EXECUTE permission on the **sp_send_dbmail** stored procedure is only granted to members of the **DatabaseMailUserRole**. A system administrator must add the user to the **DatabaseMailUserRole** database role for the user to send e-mail messages.  
  
 Profiles improve reliability in cases where an e-mail server becomes unreachable or unable to process messages. Each account in the profile has a sequence number. The sequence number determines the order in which Database Mail uses accounts in the profile. For a new e-mail message, Database Mail uses the last account that sent a message successfully, or the account that has the lowest sequence number if no message has yet been sent. Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails. If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the **AccountRetryDelay** parameter of **sysmail_configure_sp**, then starts the process of attempting to send the mail again, starting with the lowest sequence number. Use the **AccountRetryAttempts** parameter of **sysmail_configure_sp**, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.  
  
 If more than one account exists with the same sequence number, Database Mail only uses one of those accounts for a given e-mail message. In this case, Database Mail makes no guarantees as to which of the accounts is used for that sequence number or that the same account is used from message to message.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="RelatedTasks"></a> Database Mail Configuration Tasks  
 The following table describes the Database Mail configuration tasks.  
  
|Configuration Task|Topic Link|  
|------------------------|----------------|  
|Describes how to create a Database Mail accounts|[Create a Database Mail Account](../../Topics/TopicNameContainA/Create-a-Database-Mail-Account.md)|  
|Describes how to Create Database Mail profiles|[Create a Database Mail Profile](../../Topics/TopicNameContainA/Create-a-Database-Mail-Profile.md)|  
|Describes how to Configure Database mail|[Configure Database Mail](../../Topics/TopicNameNotContainA/Configure-Database-Mail.md)|  
|Describes how to create a Database Mail configuration script using templates||  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="Add_Tasks"></a> Additional Database Configuration Tasks (System Stored Procedures)  
 Database Mail configuration stored procedures are located in the **msdb** database.  
  
 The following tables list the stored procedures used for configuring and managing Database Mail.  
  
### Database Mail Settings  
  
|Name|Description|  
|----------|-----------------|  
|[sysmail_configure_sp (Transact-SQL)](assetId:///73b33c56-2bff-446a-b495-ae198ad74db1)|Changes configuration settings for Database Mail.|  
|[sysmail_help_configure_sp (Transact-SQL)](assetId:///e598d4c8-3041-4965-b046-dce3a8e3d3e0)|Displays configuration settings for Database Mail.|  
  
### Accounts and Profiles  
  
|Name|Description|  
|----------|-----------------|  
|[sysmail_add_profileaccount_sp (Transact-SQL)](assetId:///7cbf430f-1997-45ea-9707-0086184de744)|Adds a mail account to a Database Mail profile.|  
|[sysmail_delete_account_sp (Transact-SQL)](assetId:///2adcac78-4a4a-407e-9666-1d9c43c73cc2)|Deletes a Database Mail account.|  
|[sysmail_delete_profile_sp (Transact-SQL)](assetId:///71998653-4a02-446d-b6f7-50646a29e8a2)|Deletes a Database Mail profile.|  
|[sysmail_delete_profileaccount_sp (Transact-SQL)](assetId:///b58d06f2-d6c9-4c8e-95bd-027c50f4621a)|Removes an account from a Database Mail profile.|  
|[sysmail_help_account_sp (Transact-SQL)](assetId:///87c7c39c-8e05-4e68-9272-45f908809c3b)|Lists information about Database Mail accounts.|  
|[sysmail_help_profile_sp (Transact-SQL)](assetId:///d7169a8e-92b1-49eb-9124-3b2f69755ddb)|Lists information about one or more Database Mail profiles.|  
|[sysmail_help_profileaccount_sp (Transact-SQL)](assetId:///3ea68271-0a6b-4d77-991c-4757f48f747a)|Lists the accounts associated with one or more Database Mail profiles.|  
|[sysmail_update_account_sp (Transact-SQL)](assetId:///ba2fdccc-5ed4-40ef-a479-79497b4d61aa)|Updates the information in an existing Database Mail account.|  
|[sysmail_update_profile_sp (Transact-SQL)](assetId:///eaedf7ce-a8d5-4ab9-99e0-d77d5be19e90)|Changes the description or name of a Database Mail profile.|  
|[sysmail_update_profileaccount_sp (Transact-SQL)](assetId:///92ca7488-29db-414e-8e36-08b0a8f542bb)|Updates the sequence number of an account within a Database Mail profile.|  
  
### Security  
  
|Name|Description|  
|----------|-----------------|  
|[sysmail_add_principalprofile_sp (Transact-SQL)](assetId:///b2a0b313-abb9-4c23-8511-db77ca8172b3)|Grants permission for a database principal to use a Database Mail profile.|  
|[sysmail_delete_principalprofile_sp (Transact-SQL)](assetId:///8fc14700-e17a-4073-9a96-7fc23e775c69)|Removes permission for a database user to use a public or private Database Mail profile.|  
|[sysmail_help_principalprofile_sp (Transact-SQL)](assetId:///0cfd6464-09c7-4f03-9d25-58001c096a9e)|Lists Database Mail profile information for a given database user.|  
|[sysmail_update_principalprofile_sp (Transact-SQL)](assetId:///9fe96e9a-4758-4e4a-baee-3e1217c4426c)|Updates the permission information for a given database user.|  
  
### System State  
  
|Name|Description|  
|----------|-----------------|  
|[sysmail_start_sp (Transact-SQL)](assetId:///25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5)|Starts the Database Mail external program and the associated SQL Service Broker queue.|  
|[sysmail_stop_sp (Transact-SQL)](assetId:///045ee36f-5bf0-4626-b5ee-e84db06ce16f)|Stops the Database Mail external program and the associated SQL Service Broker queue.|  
|[sysmail_help_status_sp (Transact-SQL)](assetId:///b44277c6-81e8-4b4d-85b3-a2f04d602e7a)|Indicates if Database Mail is started.|  
  
##  <a name="RelatedContent"></a> Additional References  
  
-   [Database Mail Log and Audits](../../Topics/TopicNameNotContainA/Database-Mail-Log-and-Audits.md)  
  
 [&#91;Top&#93;](#Top)