---
title: "Deliver a Snapshot Through FTP"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
caps.latest.revision: 47
caps.handback.revision: 0
manager: jhubbard
---
# Deliver a Snapshot Through FTP
This topic describes how to deliver a snapshot through FTP in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To deliver a snapshot through FTP, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The Snapshot Agent must have write permissions for the directory you specify, and the Distribution Agent or Merge Agent must have read permissions. If pull subscriptions are used, you must specify a shared directory as a universal naming convention (UNC) path, such as \\\ftpserver\home\snapshots. For more information, see [Secure the Snapshot Folder](../../Topics/TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   To transfer snapshot files using File Transfer Protocol (FTP), you must first configure an FTP server. For more information, see the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Internet Information Services (IIS) documentation.  
  
###  <a name="Security"></a> Security  
 To help improve security, we recommend that you implement a virtual private network (VPN) when using FTP snapshot delivery over the Internet. For more information, see [Publish Data over the Internet Using VPN](../../Topics/TopicNameNotContainA/Publish-Data-over-the-Internet-Using-VPN.md).  
  
 As a security best practice, do not allow anonymous logins to the FTP server. The Snapshot Agent must have write permissions for the directory you specify, and the Distribution Agent or Merge Agent must have read permissions. If pull subscriptions are used, you must specify a shared directory as a universal naming convention (UNC) path, such as \\\ftpserver\home\snapshots. For more information, see [Secure the Snapshot Folder](../../Topics/TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
 When possible, prompt users to enter their credentials at runtime. If you store credentials in a script file, you must secure the file.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 After the FTP server is configured, specify directory and security information for this server in the **Publication Properties <Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To specify FTP information  
  
1.  In the **Publication Properties - <Publication\>** dialog box, select **Allow Subscribers to download snapshot files using FTP** from one of the following pages:  
  
    -   The **FTP Snapshot** page, for snapshot and transactional publications, and merge publications for Publishers running versions prior to [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)].  
  
    -   The **FTP Snapshot and Internet** page, for merge publications from Publishers running [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] or later.  
  
2.  Specify values for **FTP server name**, **Port number**, **Path from the FTP root folder**, **Login**, and **Password**.  
  
     For example, if the FTP server root is \\\ftpserver\home and you want snapshots to be stored at \\\ftpserver\home\snapshots, specify \snapshots\ftp for the property **Path from the FTP root folder** (replication appends 'ftp' to the snapshot folder path when it creates snapshot files).  
  
3.  Specify that the Snapshot Agent should write the snapshot files to the directory specified in step 2. For example, to have the Snapshot Agent write the snapshot files to \\\ftpserver\home\snapshots\ftp, you must specify the path \\\ftpserver\home\snapshots in one of two places:  
  
    -   The default snapshot location for the Distributor associated with this publication.  
  
         For more information about specifying the default snapshot location, see [Specify the Default Snapshot Location (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Specify-the-Default-Snapshot-Location--SQL-Server-Management-Studio-.md).  
  
    -   An alternate snapshot folder location for this publication. An alternate location is required if the snapshot is compressed.  
  
         Enter the path in the **Put files in the following folder** textbox on the Snapshot page of the **Publication Properties - <Publication\>** dialog box. For more information about alternate snapshot folder locations, see [Alternate Snapshot Folder Locations](../../Topics/TopicNameNotContainA/Alternate-Snapshot-Folder-Locations.md).  
  
4.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 The option to make snapshot files available on an FTP server can be set and these FTP settings can be modified programmatically using replication stored procedures. The procedure used depends on the type of publication. FTP snapshot delivery is only used with pull subscriptions.  
  
#### To enable FTP snapshot delivery for a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp_addpublication](assetId:///c7167ed1-2b7e-4824-b82b-65f4667c4407). Specify **@publication**, a value of **true** for **@enabled_for_internet**, and appropriate values for the following parameters:  
  
    -   **@ftp_address** - the address of the FTP server used to deliver the snapshot.  
  
    -   (Optional) **@ftp_port** - the port used by the FTP server.  
  
    -   (Optional) **@ftp_subdirectory** - the subdirectory of the default FTP directory assigned to an FTP login. For example, if the FTP server root is \\\ftpserver\home and you want snapshots to be stored at \\\ftpserver\home\snapshots, specify **\snapshots\ftp** for **@ftp_subdirectory** (replication appends 'ftp' to the snapshot folder path when it creates snapshot files).  
  
    -   (Optional) **@ftp_login** - a login account used when connecting to the FTP server.  
  
    -   (Optional) **@ftp_password** - the password for the FTP login.  
  
     This creates a publication that uses FTP. For more information, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md).  
  
#### To enable FTP snapshot delivery for a merge publication  
  
1.  At the Publisher on the publication database, execute [sp_addmergepublication](assetId:///28a629a1-7374-4614-9b04-279d290a942a). Specify **@publication**, a value of **true** for **@enabled_for_internet** and appropriate values for the following parameters:  
  
    -   **@ftp_address** - the address of the FTP server used to deliver the snapshot.  
  
    -   (Optional) **@ftp_port** - the port used by the FTP server.  
  
    -   (Optional) **@ftp_subdirectory** - the subdirectory of the default FTP directory assigned to an FTP login. For example, if the FTP server root is \\\ftpserver\home and you want snapshots to be stored at \\\ftpserver\home\snapshots, specify **\snapshots\ftp** for **@ftp_subdirectory** (replication appends 'ftp' to the snapshot folder path when it creates snapshot files).  
  
    -   (Optional) **@ftp_login** - a login account used when connecting to the FTP server.  
  
    -   (Optional) **@ftp_password** - the password for the FTP login.  
  
     This creates a publication that uses FTP. For more information, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md).  
  
#### To create a pull subscription to a snapshot or transactional publication that uses FTP snapshot delivery  
  
1.  At the Subscriber on the subscription database, execute [sp_addpullsubscription](assetId:///0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f). Specify **@publisher** and **@publication**.  
  
    -   At the Subscriber on the subscription database, execute [sp_addpullsubscription_agent](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b). Specify **@publisher**, **@publisher_db**, **@publication**, the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_login** and **@job_password**, and a value of **true** for **@use_ftp**.  
  
2.  At the Publisher on the publication database, execute [sp_addsubscription](assetId:///61ddf287-1fa0-4c1a-8657-ced50cebf0e0) to register the pull subscription. For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
#### To create a pull subscription to a merge publication that uses FTP snapshot delivery  
  
1.  At the Subscriber on the subscription database, execute [sp_addmergepullsubscription](assetId:///d63909a0-8ea7-4734-9ce8-8204d936a3e4). Specify **@publisher** and **@publication**.  
  
2.  At the Subscriber on the subscription database, execute [sp_addmergepullsubscription_agent](assetId:///a2f4b086-078d-49b5-8971-8a1e3f6a6feb). Specify **@publisher**, **@publisher_db**, **@publication**, the Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_login** and **@job_password**, and a value of **true** for **@use_ftp**.  
  
3.  At the Publisher on the publication database, execute [sp_addmergesubscription](assetId:///a191d817-0132-49ff-93ca-76f13e609b38) to register the pull subscription. For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
#### To change one or more FTP snapshot delivery settings for a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp_changepublication](assetId:///c36e5865-25d5-42b7-b045-dc5036225081). Specify one of the following values for **@property** and a new value of this setting for **@value**:  
  
    -   **ftp_address** - the address of the FTP server used to deliver the snapshot.  
  
    -   **ftp_port** - the port used by the FTP server.  
  
    -   **ftp_subdirectory** - the subdirectory of the default FTP directory used for the FTP snapshot.  
  
    -   **ftp_login** - a login used to connect to the FTP server.  
  
    -   **ftp_password** - the password for the FTP login.  
  
2.  (Optional) Repeat step 1 for each FTP setting being changed.  
  
3.  (Optional) To disable FTP snapshot delivery, execute [sp_changepublication](assetId:///c36e5865-25d5-42b7-b045-dc5036225081) at the Publisher on the publication database. Specify a value of **enabled_for_internet** for **@property** and a value of **false** for **@value**.  
  
#### To change FTP snapshot delivery settings for a merge publication  
  
1.  At the Publisher on the publication database, execute [sp_changemergepublication](assetId:///81fe1994-7678-4852-980b-e02fedf1e796). Specify one of the following values for **@property** and a new value of this setting for **@value**:  
  
    -   **ftp_address** - the address of the FTP server used to deliver the snapshot.  
  
    -   **ftp_port** - the port used by the FTP server.  
  
    -   **ftp_subdirectory** - the subdirectory of the default FTP directory used for the FTP snapshot.  
  
    -   **ftp_login** - a login used to connect to the FTP server.  
  
    -   **ftp_password** - the password for the FTP login.  
  
2.  (Optional) Repeat step 1 for each FTP setting being changed.  
  
3.  (Optional) To disable FTP snapshot delivery, execute [sp_changemergepublication](assetId:///81fe1994-7678-4852-980b-e02fedf1e796) at the Publisher on the publication database. Specify a value of **enabled_for_internet** for **@property** and a value of **false** for **@value**.  
  
###  <a name="TsqlExample"></a> Examples (Transact-SQL)  
 The following example creates a merge publication that allows Subscribers to access the snapshot data using FTP. The Subscriber should use a secure VPN connection when accessing the FTP share. **sqlcmd** scripting variables are used to supply login and password values. For more information, see [Use sqlcmd with Scripting Variables](../../Topics/TopicNameNotContainA/Use-sqlcmd-with-Scripting-Variables.md).  
  
 [!CODE [HowTo#sp_createmergepub_ftp](../CodeSnippet/SQL15/replication/howto#sp_createmergepub_ftp)]  
  
 The following example creates a subscription to a merge publication, where the Subscriber obtains the snapshot using FTP. The Subscriber should use a secure VPN connection when accessing the FTP share. **sqlcmd** scripting variables are used to supply login and password values. For more information, see [Use sqlcmd with Scripting Variables](../../Topics/TopicNameNotContainA/Use-sqlcmd-with-Scripting-Variables.md).  
  
 [!CODE [HowTo#sp_createmergepullsub_ftp](../CodeSnippet/SQL15/replication/howto#sp_createmergepullsub_ftp)]  
  
 [!CODE [HowTo#sp_createmergepullsubagent_ftp](../CodeSnippet/SQL15/replication/howto#sp_createmergepullsubagent_ftp)]  
  
## See Also  
 [Programming Replication Using System Stored Procedures](assetId:///816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a)   
 [Transfer Snapshots Through FTP](../../Topics/TopicNameNotContainA/Transfer-Snapshots-Through-FTP.md)   
 [Change Publication and Article Properties](../../Topics/TopicNameNotContainA/Change-Publication-and-Article-Properties.md)   
 [Initialize a Subscription with a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)