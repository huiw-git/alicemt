---
title: Manage Metadata When Making a Database Available on Another Server Instance (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d98cf2a-9fc2-4610-be72-b422b8682681
---
# Manage Metadata When Making a Database Available on Another Server Instance (SQL Server)
This topic is relevant in the following situations:  
  
-   Configuring the availability replicas of an [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] availability group.  
  
-   Setting up database mirroring for a database.  
  
-   When preparing to change roles between primary and secondary servers in a log shipping configuration.  
  
-   Restoring a database to another server instance.  
  
-   Attaching a copy of a database on another server instance.  
  
 Some applications depend on information, entities, and/or objects that are outside of the scope of a single user database. Typically, an application has dependencies on the **master** and **msdb** databases, and also on the user database. Anything stored outside of a user database that is required for the correct functioning of that database must be made available on the destination server instance. For example, the logins for an application are stored as metadata in the **master** database, and they must be re-created on the destination server. If an application or database maintenance plan depends on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent jobs, whose metadata is stored in the **msdb** database, you must re-create those jobs on the destination server instance. Similarly, the metadata for a server-level trigger is stored in **master**.  
  
 When you move the database for an application to another server instance, you must re-create all the metadata of the dependant entities and objects in **master** and **msdb** on the destination server instance. For example, if a database application uses server-level triggers, just attaching or restoring the database on the new system is not enough. The database will not work as expected unless you manually re-create the metadata for those triggers in the **master** database.  
  
##  <a name="information_entities_and_objects"></a> Information, Entities, and Objects That Are Stored Outside of User Databases  
 The remainder of this topic summarizes the potential issues that might affect a database that is being made available on another server instance. You might have to re-create one or more of the types of information, entities, or objects listed in the following list. To see a summary, click the link for the item.  
  
-   [Server configuration settings](#server_configuration_settings)  
  
-   [Credentials](#credentials)  
  
-   [Cross-database queries](#cross_database_queries)  
  
-   [Database ownership](#database_ownership)  
  
-   [Distributed queries/linked servers](#distributed_queries_and_linked_servers)  
  
-   [Encrypted data](#encrypted_data)  
  
-   [User-defined error messages](#user_defined_error_messages)  
  
-   [Event notifications and Windows Management Instrumentation (WMI) events (at server level)](#event_notif_and_wmi_events)  
  
-   [Extended stored procedures](#extended_stored_procedures)  
  
-   [Full-text engine for SQL Server properties](#ifts_service_properties)  
  
-   [Jobs](#jobs)  
  
-   [Logins](#logins)  
  
-   [Permissions](#permissions)  
  
-   [Replication settings](#replication_settings)  
  
-   [Service Broker applications](#sb_applications)  
  
-   [Startup procedures](#startup_procedures)  
  
-   [Triggers (at server level)](#triggers)  
  
##  <a name="server_configuration_settings"></a> Server Configuration Settings  
 [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/includes/ssVersion2005_md.md)] and later versions selectively install and starts key services and features. This helps reduce the attackable surface area of a system. In the default configuration of new installations, many features are not enabled. If the database relies on any service or feature that is off by default, this service or feature must be enabled on the destination server instance.  
  
 For more information about these settings and enabling or disabling them, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="credentials"></a> Credentials  
 A credential is a record that contains the authentication information that is required to connect to a resource outside [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. Most credentials consist of a Windows login and password.  
  
 For more information about this feature, see [Credentials (Database Engine)](../../Topics/TopicNameNotContainA/Credentials--Database-Engine-.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent Proxy accounts use credentials. To learn the credential ID of a proxy account, use the [sysproxies](assetId:///a73da875-be22-45fc-b5e2-ea7ebd48e2d6) system table.  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="cross_database_queries"></a> Cross-Database Queries  
 The DB_CHAINING and TRUSTWORTHY database options are OFF by default. If either of these is set to ON for the original database, you may have to enable them on the database on the destination server instance. For more information, see [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da).  
  
 Attach-and-detach operations disable cross-database ownership chaining for the database. For information about how to enable chaining, see [cross db ownership chaining Server Configuration Option](../../Topics/TopicNameNotContainA/cross-db-ownership-chaining-Server-Configuration-Option.md).  
  
 For more information, see also [Set Up a Mirror Database to Use the Trustworthy Property (Transact-SQL)](../../Topics/TopicNameContainA/Set-Up-a-Mirror-Database-to-Use-the-Trustworthy-Property--Transact-SQL-.md)  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="database_ownership"></a> Database Ownership  
 When a database is restored on another computer, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] login or Windows user who initiated the restore operation becomes the owner of the new database automatically. When the database is restored, the system administrator or the new database owner can change database ownership.  
  
##  <a name="distributed_queries_and_linked_servers"></a> Distributed Queries and Linked Servers  
 Distributed queries and linked servers are supported for OLE DB applications. Distributed queries access data from multiple heterogeneous data sources on either the same or different computers. A linked server configuration enables [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] to execute commands against OLE DB data sources on remote servers. For more information about these features, see [Linked Servers (Database Engine)](../../Topics/TopicNameNotContainA/Linked-Servers--Database-Engine-.md).  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="encrypted_data"></a> Encrypted Data  
 If the database you are making available on another server instance contains encrypted data and if the database master key is protected by the service master key on the original server, it might be necessary to re-create the service master key encryption. The *database master key* is a symmetric key that is used to protect the private keys of certificates and asymmetric keys in an encrypted database. When created, the database master key is encrypted by using the Triple DES algorithm and a user-supplied password.  
  
 To enable the automatic decryption of the database master key on a server instance, a copy of this key is encrypted by using the service master key. This encrypted copy is stored in both the database and in **master**. Typically, the copy stored in **master** is silently updated whenever the master key is changed. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] first tries to decrypt the database master key with the service master key of the instance. If that decryption fails, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] searches the credential store for master key credentials that have the same family GUID as the database for which it requires the master key. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] then tries to decrypt the database master key with each matching credential until the decryption succeeds or there are no more credentials. A master key that is not encrypted by the service master key must be opened by using the OPEN MASTER KEY statement and a password.  
  
 When an encrypted database is copied, restored, or attached to a new instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], a copy of the database master key encrypted by the service master key is not stored in **master** on the destination server instance. On the destination server instance, you must open the master key of the database. To open the master key, execute the following statement: OPEN MASTER KEY DECRYPTION BY PASSWORD **= '***password***'**. We recommend that you then enable automatic decryption of the database master key by executing the following statement: ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY. This ALTER MASTER KEY statement provisions the server instance with a copy of the database master key that is encrypted with the service master key. For more information, see [OPEN MASTER KEY (Transact-SQL)](assetId:///1674753e-ca1e-4913-9ba4-b442e7106121) and [ALTER MASTER KEY (Transact-SQL)](assetId:///8ac501c3-4280-4d5b-b58a-1524fa715b50).  
  
 For information about how to enable automatic decryption of the database master key of a mirror database, see [Set Up an Encrypted Mirror Database](../../Topics/TopicNameNotContainA/Set-Up-an-Encrypted-Mirror-Database.md).  
  
 For more information, see also:  
  
-   [Encryption Hierarchy](../../Topics/TopicNameNotContainA/Encryption-Hierarchy.md)  
  
-   [Set Up an Encrypted Mirror Database](../../Topics/TopicNameNotContainA/Set-Up-an-Encrypted-Mirror-Database.md)  
  
-   [Create Identical Symmetric Keys on Two Servers](../../Topics/TopicNameNotContainA/Create-Identical-Symmetric-Keys-on-Two-Servers.md)  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="user_defined_error_messages"></a> User-defined Error Messages  
 User-defined error messages reside in the [sys.messages](assetId:///8c16ecdf-68f4-4a2a-b594-086e3344e58a) catalog view. This catalog view is stored in **master**. If a database application depends on user-defined error messages and the database is made available on another server instance, use [sp_addmessage](assetId:///54746d30-f944-40e5-a707-f2d9be0fb9eb) to add those user-defined messages on the destination server instance.  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="event_notif_and_wmi_events"></a> Event Notifications and Windows Management Instrumentation (WMI) Events (at Server Level)  
  
### Server-Level Event Notifications  
 Server-level event notifications are stored in **msdb**. Therefore, if a database application relies on a server-level event notifications, that event notification must be re-created on the destination server instance. To view the event notifications on a server instance, use the [sys.server_event_notifications](assetId:///1a83a044-3130-4551-95ca-162525846ff5) catalog view. For more information, see [Event Notifications](../../Topics/TopicNameNotContainA/Event-Notifications.md).  
  
 Additionally, event notifications are delivered by using [!INCLUDE[ssSB](../../Topics/TopicNameContainA/includes/ssSB_md.md)]. Routes for incoming messages are not included in the database that contains a service. Instead, explicit routes are stored in **msdb**. If your service uses an explicit route in the **msdb** database to route incoming messages to the service, when you attach a database in a different instance, you must re-create this route.  
  
### Windows Management Instrumentation (WMI) Events  
 The WMI Provider for Server Events lets you use the Windows Management Instrumentation (WMI) to monitor events in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. Any application that relies on server-level events exposed through the WMI provider on which a database relies must be defined the computer of the destination server instance. WMI Event provider creates event notifications with a target service that is defined in **msdb**.  
  
> [!NOTE]  
>  For more information, see [WMI Provider for Server Events](assetId:///80767fe0-32ac-406a-81a0-8212cd6ce7e4).  
  
 **To create a WMI alert using SQL Server Management Studio**  
  
-   [How to: Create a WMI Event Alert (SQL Server Management Studio)](assetId:///b8c46db6-408b-484e-98f0-a8af3e7ec763)  
  
### How Event Notifications Work for a Mirrored Database  
 Cross-database delivery of event notifications that involves a mirrored database is remote, by definition, because the mirrored database can fail over. [!INCLUDE[ssSB](../../Topics/TopicNameContainA/includes/ssSB_md.md)] provides special support for mirrored databases, in the form of *mirrored routes*. A mirrored route has two addresses: one for the principal server instance and one for the mirror server instance.  
  
 By setting up mirrored routes, you make [!INCLUDE[ssSB](../../Topics/TopicNameContainA/includes/ssSB_md.md)] routing aware of database mirroring. The mirrored routes enable [!INCLUDE[ssSB](../../Topics/TopicNameContainA/includes/ssSB_md.md)] to transparently redirect conversations to the current principal server instance. For example, consider a service, Service_A, which is hosted by a mirrored database, Database_A. Assume that you need another service, Service_B, which is hosted by Database_B, to have a dialog with Service_A. For this dialog to be possible, Database_B must contain a mirrored route for Service_A. In addition, Database_A must contain a nonmirrored TCP transport route to Service_B, which, unlike a local route, remains valid after failover. These routes enable ACKs to come back after a failover. Because the service of the sender is always named in the same manner, the route must specify the broker instance.  
  
 The requirement for mirrored routes applies for regardless of whether the service in the mirrored database is the initiator service or the target service:  
  
-   If target service is in the mirrored database, the initiator service must have a mirrored route back to the target. However, the target can have a regular route back to initiator.  
  
-   If initiator service is in the mirrored database, the target service must have a mirrored route back to initiator to deliver acknowledgements and replies. However, the initiator can have a regular route to the target.  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="extended_stored_procedures"></a> Extended Stored Procedures  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/includes/ssNoteDepFutureAvoid_md.md)] Use [CLR Integration](assetId:///7be9e644-36a2-48fc-9206-faf59fdff4d7) instead.  
  
 Extended stored procedures are programmed by using the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Extended Stored Procedure API. A member of the **sysadmin** fixed server role can register an extended stored procedure with an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] and grant permission to users to execute the procedure. Extended stored procedures can be added only to the **master** database.  
  
 Extended stored procedures run directly in the address space of an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], and they may produce memory leaks or other problems that reduce the performance and reliability of the server. You should consider storing extended stored procedures in an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] that is separate from the instance that contains the referenced data. You should also consider using distributed queries to access the database.  
  
> [!IMPORTANT]  
>  Before adding extended stored procedures to the server and granting EXECUTE permissions to other users, the system administrator should thoroughly review each extended stored procedure to make sure that it does not contain harmful or malicious code.  
  
 For more information, see [GRANT Object Permissions (Transact-SQL)](assetId:///c001c2e7-d092-43d4-8fa6-693b3ec4c3ea), [DENY Object Permissions (Transact-SQL)](assetId:///0b8d3ddc-38c0-4241-b7bb-ee654a5081aa), and [REVOKE Object Permissions (Transact-SQL)](assetId:///99c7146e-d2e7-4f1a-80ff-21a05bc5e8bb).  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="ifts_service_properties"></a> Full-Text Engine for SQL Server Properties  
 Properties are set on the Full-Text Engine by [sp_fulltext_service](assetId:///17a91433-f9b6-4a40-88c4-8c704ec2de9f). Make sure that the destination server instance has the required settings for these properties. For more information about these properties, see [FULLTEXTSERVICEPROPERTY (Transact-SQL)](assetId:///b7dcacb0-af83-4807-9d1e-49148b56b59c).  
  
 Additionally, if the [word breakers and stemmers](../../Topics/TopicNameNotContainA/Configure-and-Manage-Word-Breakers-and-Stemmers-for-Search.md) component or [full-text search filters](../../Topics/TopicNameNotContainA/Configure-and-Manage-Filters-for-Search.md) component have different versions on the original and destination server instances, full-text index and queries may behave differently. Also, the [thesaurus](../../Topics/TopicNameNotContainA/Configure-and-Manage-Thesaurus-Files-for-Full-Text-Search.md) is stored in instance-specific files. You must either transfer a copy of those files to an equivalent location on the destination server instance or re-create them on new instance.  
  
> [!NOTE]  
>  When you attach a [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/includes/ssVersion2005_md.md)] database that contains full-text catalog files onto a [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] server instance, the catalog files are attached from their previous location along with the other database files, the same as in [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/includes/ssVersion2005_md.md)]. For more information, see [Upgrade Full-Text Search](../../Topics/TopicNameNotContainA/Upgrade-Full-Text-Search.md).  
  
 For more information, see also:  
  
-   [Back Up and Restore Full-Text Catalogs and Indexes](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Full-Text-Catalogs-and-Indexes.md)  
  
-   [Database Mirroring and Full-Text Catalogs (SQL Server)](../../Topics/TopicNameNotContainA/Database-Mirroring-and-Full-Text-Catalogs--SQL-Server-.md)  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="jobs"></a> Jobs  
 If the database relies on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent jobs, you will have to re-create them on the destination server instance. Jobs depend on their environments. If you plan to re-create an existing job on the destination server instance, the destination server instance might have to be modified to match the environment of that job on the original server instance. The following environmental factors are significant:  
  
-   The login used by the job  
  
     To create or execute [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent jobs, you must first add any [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] logins required by the job to the destination server instance. For more information, see [How to: Configure a User to Create and Manage SQL Server Agent Jobs (SQL Server Management Studio)](assetId:///67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef).  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent service startup account  
  
     The service startup account defines the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] Windows account in which [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent runs and its network permissions. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent runs as a specified user account. The context of the Agent service affects the settings for the job and its run environment. The account must have access to the resources, such as network shares, required by the job. For information about how to select and modify the service startup account, see [Selecting an Account for the SQL Server Agent Service](assetId:///fe658e32-9e6b-4147-a189-7adc3bd28fe7).  
  
     To operate correctly, the service startup account must be configured to have the correct domain, file system, and registry permissions. Also, a job might require a shared network resource that must be configured for the service account. For information, see [Configure Windows Service Accounts and Permissions](../../Topics/TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent service, which is associated with a specific instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], has its own registry hive, and its jobs typically have dependencies on one or more of the settings in this registry hive. To behave as intended, a job requires those registry settings. If you use a script to re-create a job in another [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent service, its registry might not have the correct settings for that job. For re-created jobs to behave correctly on a destination server instance, the original and destination [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent services should have the same registry settings.  
  
    > [!CAUTION]  
    >  Changing registry settings on the destination [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent service to handle a re-created job could be problematic if the current settings are required by other jobs. Furthermore, incorrectly editing the registry can severely damage your system. Before you make changes to the registry, we recommend that you back up any valued data on the computer.  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent Proxies  
  
     A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent proxy defines the security context for a specified job step. For a job to run on the destination server instance, all the proxies it requires must be manually re-created on that instance. For more information, see [Create a SQL Server Agent Proxy](assetId:///142e0c55-a8b9-4669-be49-b9dc602d5988) and [Troubleshooting Multiserver Jobs That Use Proxies](assetId:///fc579bd3-010c-4f72-8b5c-d0cc18a1f280).  
  
 For more information, see also:  
  
-   [Implementing Jobs](assetId:///69e06724-25c7-4fb3-8a5b-3d4596f21756)  
  
-   [Management of Logins and Jobs After Role Switching (SQL Server)](../../Topics/TopicNameNotContainA/Management-of-Logins-and-Jobs-After-Role-Switching--SQL-Server-.md) (for database mirroring)  
  
-   [Configure Windows Service Accounts and Permissions](../../Topics/TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md) (when you install an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)])  
  
-   [Configuring SQL Server Agent](assetId:///2e361a62-9e92-4fcd-80d7-d6960f127900) (when you install an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)])  
  
-   [Implementing SQL Server Agent Security](assetId:///d770d35c-c8de-4e00-9a85-7d03f45a0f0d)  
  
 **To view existing jobs and their properties**  
  
-   [Monitoring Job Activity](assetId:///71cb432b-631d-4b8b-9965-e731b3d8266d)  
  
-   [sp_help_job (Transact-SQL)](assetId:///8a8b6104-e0e4-4d07-a2c3-f4243ee0d6fa)  
  
-   [How to: View Job Step Information (SQL Server Management Studio)](assetId:///e3f06492-dc86-4e06-b186-ea58aff6d591)  
  
-   [sysjobs (Transact-SQL)](assetId:///e244a6a5-54c2-47a6-8039-dd1852b0ae59)  
  
 **To create a job**  
  
-   [How to: Create a Job (SQL Server Management Studio)](assetId:///b35af2b6-6594-40d1-9861-4d5dd906048c)  
  
-   [Create a Job](assetId:///b35af2b6-6594-40d1-9861-4d5dd906048c)  
  
#### Best Practices for Using a Script to Re-create a Job  
 We recommend that you start by scripting a simple job, re-creating the job on the other [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent service, and running the job to see whether it works as intended. This will let you to identify incompatibilities and try to resolve them. If a scripted job does not work as intended in its new environment, we recommend that you create an equivalent job that works correctly in that environment.  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="logins"></a> Logins  
 Logging into an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] requires a valid [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] login. This login is used in the authentication process that verifies whether the principal can connect to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. A database user for which the corresponding [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] login is undefined or is incorrectly defined on a server instance cannot log in to the instance. Such a user is said to be an *orphaned user* of the database on that server instance. A database user can become orphaned if after a database is restored, attached, or copied to a different instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)].  
  
 To generate a script for some or all the objects in the original copy of the database, you can use the Generate Scripts Wizard, and in the **Choose Script Options** dialog box, set the **Script Logins** option to **True**.  
  
> [!NOTE]  
>  For information about how to set up logins for a mirrored database, see [Set Up Login Accounts for Database Mirroring or Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Set-Up-Login-Accounts-for-Database-Mirroring-or-Always-On-Availability-Groups--SQL-Server-.md) and [Management of Logins and Jobs After Role Switching (SQL Server)](../../Topics/TopicNameNotContainA/Management-of-Logins-and-Jobs-After-Role-Switching--SQL-Server-.md).  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="permissions"></a> Permissions  
 The following types of permissions might be affected when a database is made available on another server instance.  
  
-   GRANT, REVOKE, or DENY permissions on system objects  
  
-   GRANT, REVOKE, or DENY permissions on server instance (*server-level permissions*)  
  
### GRANT, REVOKE, and DENY Permissions on System Objects  
 Permissions on system objects such as stored procedures, extended stored procedures, functions, and views, are stored in the **master** database and must be configured on the destination server instance.  
  
 To generate a script for some or all the objects in the original copy of the database, you can use the Generate Scripts Wizard, and in the **Choose Script Options** dialog box, set the **Script Object-Level Permissions** option to **True**.  
  
> [!IMPORTANT]  
>  If you script logins, the passwords are not scripted. If you have logins that use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Authentication, you have to modify the script on the destination.  
  
 System objects are visible in the [sys.system_objects](assetId:///069e9045-97f2-4463-8e8f-c73855f3ea0a) catalog view. The permissions on system objects are visible in the [sys.database_permissions](assetId:///c1e261f8-6cb0-4759-b5f1-5ec233602655) catalog view in the **master** database. For information about querying these catalog views and granting system-object permissions, see [GRANT System Object Permissions (Transact-SQL)](assetId:///9d4e89f4-478f-419a-8b50-b096771e3880). For more information, see [REVOKE System Object Permissions (Transact-SQL)](assetId:///84983238-dd7d-45bd-99bb-52c9d8e96a87) and [DENY System Object Permissions (Transact-SQL)](assetId:///4e43f954-0982-470b-a239-08a13c61563a).  
  
### GRANT, REVOKE, and DENY Permissions on a Server Instance  
 Permissions at the server scope are stored in the **master** database and must be configured on the destination server instance. For information about the server permissions of a server instance, query the [sys.server_permissions](assetId:///7d78bf17-6c64-4166-bd0b-9e9e20992136) catalog view, for information about server principals query the [sys.server_principals](assetId:///c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37)s catalog view, and for information about membership of server roles query the [sys.server_role_members](assetId:///efa20414-2c6b-45a2-a7a9-60110a24da18) catalog view.  
  
 For more information, see [GRANT Server Permissions (Transact-SQL)](assetId:///7e880a5a-3bdc-491f-a167-7a9ed338be7f), [REVOKE Server Permissions (Transact-SQL)](assetId:///7b9a56b3-face-452e-a655-147dac306ba1), and [DENY Server Permissions (Transact-SQL)](assetId:///68d6b2a9-c36f-465a-9cd2-01d43a667e99).  
  
#### Server-Level Permissions for a Certificate or Asymmetric Key  
 Server-level permissions cannot be granted directly to a certificate or asymmetric key. Instead, server-level permissions are granted to a mapped login that is created exclusively for a specific certificate or asymmetric key. Therefore, each certificate or asymmetric key that requires server-level permissions, requires its own *certificate-mapped login* or *asymmetric key-mapped login*. To grant server-level permissions for a certificate or asymmetric key, grant the permissions to its mapped login.  
  
> [!NOTE]  
>  A mapped login is used only for authorization of code signed with the corresponding certificate or asymmetric key. Mapped logins cannot be used for authentication.  
  
 The mapped login and its permissions both reside in **master**. If a certificate or asymmetric key resides in a database other than **master**, you must re-create it in **master** and map it to a login. If you move, copy, or restore the database to another server instance, you must re-create its certificate or asymmetric key in the **master** database of the destination server instance, map to a login, and grant the required server-level permissions to the login.  
  
 **To create a certificate or asymmetric key**  
  
-   [CREATE CERTIFICATE (Transact-SQL)](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d)  
  
-   [CREATE ASYMMETRIC KEY (Transact-SQL)](assetId:///141bc976-7631-49f6-82bd-a235028645b1)  
  
 **To map a certificate or asymmetric key to a login**  
  
-   [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01)  
  
 **To assign permissions to the mapped login**  
  
-   [GRANT Server Permissions (Transact-SQL)](assetId:///7e880a5a-3bdc-491f-a167-7a9ed338be7f)  
  
 For more information about certificates and asymmetric keys, see [Encryption Hierarchy](../../Topics/TopicNameNotContainA/Encryption-Hierarchy.md).  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="replication_settings"></a> Replication Settings  
 If you restore a backup of a replicated database to another server or database, replication settings cannot be preserved. In this case, you must re-create all publications and subscriptions after backups are restored. To make this process easier, create scripts for your current replication settings and, also, for the enabling and disabling of replication. To help re-create your replication settings, copy these scripts and change the server name references to work for the destination server instance.  
  
 For more information, see [Back Up and Restore Replicated Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md), [Database Mirroring and Replication (SQL Server)](../../Topics/TopicNameNotContainA/Database-Mirroring-and-Replication--SQL-Server-.md), and [Log Shipping and Replication (SQL Server)](../../Topics/TopicNameNotContainA/Log-Shipping-and-Replication--SQL-Server-.md).  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="sb_applications"></a> Service Broker Applications  
 Many aspects of a [!INCLUDE[ssSB](../../Topics/TopicNameContainA/includes/ssSB_md.md)] application move with the database. However, some aspects of the application must be re-created or reconfigured in the new location.  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="startup_procedures"></a> Startup Procedures  
 A startup procedure is a stored procedure that is marked for automatic execution and is executed every time [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] starts. If the database depends on any startup procedures, they must be defined on the destination server instance and be configured to be automatically executed at startup.  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
##  <a name="triggers"></a> Triggers (at Server Level)  
 DDL triggers fire stored procedures in response to a variety of Data Definition Language (DDL) events. These events primarily correspond to [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] statements that start with the keywords CREATE, ALTER, and DROP. Certain system stored procedures that perform DDL-like operations can also fire DDL triggers.  
  
 For more information about this feature, see [DDL Triggers](../../Topics/TopicNameNotContainA/DDL-Triggers.md).  
  
 [&#91;Top&#93;](#information_entities_and_objects)  
  
## See Also  
 [Contained Databases](../../Topics/TopicNameNotContainA/Contained-Databases.md)   
 [Copy Databases to Other Servers](../../Topics/TopicNameNotContainA/Copy-Databases-to-Other-Servers.md)   
 [Database Detach and Attach (SQL Server)](../../Topics/TopicNameNotContainA/Database-Detach-and-Attach--SQL-Server-.md)   
 [Fail Over to a Log Shipping Secondary (SQL Server)](../../Topics/TopicNameContainA/Fail-Over-to-a-Log-Shipping-Secondary--SQL-Server-.md)   
 [Role Switching During a Database Mirroring Session (SQL Server)](../../Topics/TopicNameContainA/Role-Switching-During-a-Database-Mirroring-Session--SQL-Server-.md)   
 [Set Up an Encrypted Mirror Database](../../Topics/TopicNameNotContainA/Set-Up-an-Encrypted-Mirror-Database.md)   
 [SQL Server Configuration Manager](../../Topics/TopicNameNotContainA/SQL-Server-Configuration-Manager.md)   
 [Troubleshoot Orphaned Users (SQL Server)](../../Topics/TopicNameNotContainA/Troubleshoot-Orphaned-Users--SQL-Server-.md)