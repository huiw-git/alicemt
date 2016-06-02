---
title: Upgrade Replicated Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
---
# Upgrade Replicated Databases
  [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] supports upgrading replicated databases from previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]; it is not required to stop activity at other nodes while a node is being upgraded. Ensure that you adhere to the rules regarding which versions are supported in a topology:  
  
-   A Distributor can be any version as long as it is greater than or equal to the Publisher version \(in many cases the Distributor is the same instance as the Publisher\).  
  
-   A Publisher can be any version as long as it less than or equal to the Distributor version.  
  
-   Subscriber version depends on the type of publication:  
  
    -   A Subscriber to a transactional publication can be any version within two versions of the Publisher version. For example: a [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] Publisher can have [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] and [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] Subscribers; and a [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] Publisher can have [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] and  [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] Subscribers.  
  
    -   A Subscriber to a merge publication can be any version less than or equal to the Publisher version.  
  
> [!NOTE]  
>  This topic is available in the Setup Help documentation and in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online. Topic links that appear as bold text in the Setup Help documentation refer to topics that are only available in Books Online.  
  
## Run the Log Reader Agent for Transactional Replication Before Upgrade  
 Before you upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you must make sure that all committed transactions from published tables have been processed by the Log Reader Agent. To make sure that all transactions have been processed, perform the following steps for each database that contains transactional publications:  
  
1.  Make sure that the Log Reader Agent is running for the database. By default, the agent runs continuously.  
  
2.  Stop user activity on published tables.  
  
3.  Allow time for the Log Reader Agent to copy transactions to the distribution database, and then stop the agent.  
  
4.  Execute [sp\_replcmds](../Topic/sp_replcmds%20\(Transact-SQL\).md) to verify that all transactions have been processed. The result set from this procedure should be empty.  
  
5.  Execute [sp\_replflush](../Topic/sp_replflush%20\(Transact-SQL\).md) to close the connection from sp\_replcmds.  
  
6.  Perform the server upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
7.  Restart [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent and the Log Reader Agent if they do not start automatically after the upgrade.  
  
## Run Agents for Merge Replication After Upgrade  
 After upgrade, run the Snapshot Agent for each merge publication and the Merge Agent for each subscription to update replication metadata. You do not have to apply the new snapshot, because it is not necessary to reinitialize subscriptions. Subscription metadata is updated the first time the Merge Agent is run after upgrade. This means that the subscription database can remain online and active during the Publisher upgrade.  
  
 Merge replication stores publication and subscription metadata in a number of system tables in the publication and subscription databases. Running the Snapshot Agent updates publication metadata and running the Merge Agent updates subscription metadata. It is only required to generate a publication snapshot. If a merge publication uses parameterized filters, each partition also has a snapshot. It is not necessary to update these partitioned snapshots.  
  
 Run the agents from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], Replication Monitor, or from the command line. For more information about running the Snapshot Agent, see the following topics:  
  
-   [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md)  
  
-   [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md)  
  
-   [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md)  
  
 For more information about running the Merge Agent, see the following topics:  
  
-   [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md)  
  
-   [Synchronize a Push Subscription](../../Topics\TopicNameContainA/Synchronize-a-Push-Subscription.md)  
  
 After upgrading [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in a topology that uses merge replication, change the publication compatibility level of any publications if you want to use new features.  
  
## Upgrading to Standard, Workgroup, or Express Editions  
 Before upgrading from one edition of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] to another, verify that the functionality you are currently using is supported in the edition to which you are upgrading. For more information, see the section on Replication in [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
## Web Synchronization for Merge Replication  
 The Web synchronization option for merge replication requires that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Listener \(replisapi.dll\) be copied to the virtual directory on the Internet Information Services \(IIS\) server used for synchronization. When you configure Web synchronization, the file is copied to the virtual directory by the Configure Web Synchronization Wizard. If you upgrade the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components installed on the IIS server, you must manually copy replisapi.dll from the COM directory to the virtual directory on the IIS server. For more information about configuring Web synchronization, see [Configure Web Synchronization](../../Topics\TopicNameNotContainA/Configure-Web-Synchronization.md).  
  
## Restoring a Replicated Database from an Earlier Version  
 To ensure replication settings are retained when restoring a backup of a replicated database from a previous version: restore to a server and database with the same names as the server and database at which the backup was taken.  
  
## See Also  
 [Administration &#40;Replication&#41;](../Topic/Administration%20\(Replication\).md)   
 [Replication Backward Compatibility](../../Topics\TopicNameNotContainA/Replication-Backward-Compatibility.md)   
 [What's New &#40;Replication&#41;](../Topic/What's%20New%20\(Replication\).md)   
 [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md)   
 [Upgrade to SQL Server 2016](../../Topics\TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md)  
  
  