---
title: "Upgrade Replication Scripts (Replication Transact-SQL Programming)"
ms.custom: na
ms.date: 08/09/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
caps.latest.revision: 42
manager: jhubbard
---
# Upgrade Replication Scripts (Replication Transact-SQL Programming)
[!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script files can be used to programmatically configure a replication topology. For more information, see [Programming Replication Using System Stored Procedures](assetId:///816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a).  
  
> [!IMPORTANT]  
>  Although you are not required to upgrade scripts that are executed by members of the **sysadmin** role, we recommend that you modify existing scripts as described in this topic. Specify an account that has minimum permissions for each replication agent as described in the "Permissions Required By Agents" section of the topic [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
 These security improvements, which enable more control over permissions by allowing you to explicitly specify the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows accounts under which replication agent jobs are executed, affect the following stored procedures in existing scripts:  
  
-   **sp_addpublication_snapshot**:  
  
     You should now supply the Windows credentials as **@job_login** and **@job_password** when executing [sp_addpublication_snapshot](assetId:///192b6214-df6e-44a3-bdd4-9d933a981619) to create the job under which the Snapshot Agent runs at the Distributor.  
  
-   **sp_addpushsubscription_agent**:  
  
     You should now execute [sp_addpushsubscription_agent](assetId:///1fdd2052-50d8-4318-8aa7-fc635d5cad18) to explicitly add a job and supply the Windows credentials (**@job_login** and **@job_password**) under which the Distribution Agent job runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], this was done automatically when a push subscription was created.  
  
-   **sp_addmergepushsubscription_agent**:  
  
     You should now execute [sp_addmergepushsubscription_agent](assetId:///808a1925-be46-4999-8d69-b3a83010ec81) to explicitly add a job and supply the Windows credentials (**@job_login** and **@job_password**) under which the Merge Agent job runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], this was done automatically when a push subscription was created.  
  
-   **sp_addpullsubscription_agent**:  
  
     You should now supply the Windows credentials as **@job_login** and **@job_password** when executing [sp_addpullsubscription_agent](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b) to create the job under which the Distribution Agent runs at the Subscriber.  
  
-   **sp_addmergepullsubscription_agent**:  
  
     You should now supply the Windows credentials as **@job_login** and **@job_password** when executing [sp_addmergepullsubscription_agent](assetId:///a2f4b086-078d-49b5-8971-8a1e3f6a6feb) to create the job under which the Merge Agent runs at the Subscriber.  
  
-   **sp_addlogreader_agent**:  
  
     You should now execute [sp_addlogreader_agent](assetId:///d83096b9-96ee-4789-bde0-940d4765b9ed) to manually add the job and supply the Windows credentials under which the Log Reader Agent runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], this was done automatically when a transactional publication was created.  
  
-   **sp_addqreader_agent**:  
  
     You should now execute [sp_addqreader_agent](assetId:///dc9f591a-e67e-4ba8-bf47-defd5eda0822) to manually add the job and supply the Windows credentials under which the Queue Reader Agent runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], this was done automatically when a transactional publication that supported queued updating was created.  
  
 In the security model introduced in [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], replication agents always make connections to the local instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] with Windows Authentication using the credentials supplied in **@job_name** and **@job_password**. For information about the requirements of Windows accounts used when running replication agent jobs, see [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
> [!IMPORTANT]  
>  When possible, prompt users to enter security credentials at runtime. If you store credentials in a script file, ensure that the file itself is secured.  
  
### To upgrade scripts that configure a snapshot or transactional publication  
  
1.  In the existing script, before [sp_addpublication](assetId:///c7167ed1-2b7e-4824-b82b-65f4667c4407), execute [sp_addlogreader_agent](assetId:///d83096b9-96ee-4789-bde0-940d4765b9ed) at the Publisher on the publication database. Specify the Windows credentials under which the Log Reader Agent runs for **@job_name** and **@job_password**. If the agent will use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher_security_mode** and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login information for **@publisher_login** and **@publisher_password**. This creates a Log Reader Agent job for the publication database.  
  
    > [!NOTE]  
    >  This step is only for transactional publications and is not required for snapshot publications.  
  
2.  (Optional) Before [sp_addpublication](assetId:///c7167ed1-2b7e-4824-b82b-65f4667c4407), execute [sp_addqreader_agent](assetId:///dc9f591a-e67e-4ba8-bf47-defd5eda0822) at the Distributor on the distribution database. Specify the Windows credentials under which the Queue Reader Agent runs for **@job_name** and **@job_password**. This creates a Queue Reader Agent job for the Distributor.  
  
    > [!NOTE]  
    >  This step is only required for transactional publications that support queued updating subscribers.  
  
3.  (Optional) Update the execution of [sp_addpublication](assetId:///c7167ed1-2b7e-4824-b82b-65f4667c4407) to set any non-default values for parameters that implement new replication functionalities.  
  
4.  After [sp_addpublication](assetId:///c7167ed1-2b7e-4824-b82b-65f4667c4407), execute [sp_addpublication_snapshot](assetId:///192b6214-df6e-44a3-bdd4-9d933a981619) at the Publisher on the publication database. Specify **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job_name** and **@job_password**. If the agent will use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher_security_mode** and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login information for **@publisher_login** and **@publisher_password**. This creates a Snapshot Agent job for the publication.  
  
5.  (Optional) Update the execution of [sp_addarticle](assetId:///0483a157-e403-4fdb-b943-23c1b487bef0) to set any non-default values for parameters that implement new replication functionalities.  
  
### To upgrade scripts that add subscriptions to a snapshot or transactional publication  
  
1.  After executing the stored procedure that creates the subscription, ensure that you execute the stored procedure that creates a Distribution Agent job to synchronize the subscription. The stored procedure that you use will depend on the type of subscription.  
  
    -   For a pull subscription, update the execution of [sp_addpullsubscription_agent](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b) to supply the Windows credentials under which the Distribution Agent runs at the Subscriber for **@job_name** and **@job_password**. This is done after the execution of [sp_addpullsubscription](assetId:///0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f). For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
    -   For a push subscription, execute [sp_addpushsubscription_agent](assetId:///1fdd2052-50d8-4318-8aa7-fc635d5cad18) at the Publisher. Specify **@subscriber**, **@subscriber_db**, **@publication**, Windows credentials under which the Distribution Agent runs at the Distributor for **@job_name** and **@job_password**, and a schedule for this agent job. For more information, see [Specify Synchronization Schedules](../../Topics/TopicNameNotContainA/Specify-Synchronization-Schedules.md). This is done after the execution of [sp_addsubscription](assetId:///61ddf287-1fa0-4c1a-8657-ced50cebf0e0). For more information, see [Create a Push Subscription](../../Topics/TopicNameContainA/Create-a-Push-Subscription.md).  
  
### To upgrade scripts that configure a merge publication  
  
1.  (Optional) In the existing script, update the execution of [sp_addmergepublication](assetId:///28a629a1-7374-4614-9b04-279d290a942a) to set any non-default values for parameters that implement new replication functionalities.  
  
2.  After [sp_addmergepublication](assetId:///28a629a1-7374-4614-9b04-279d290a942a), execute [sp_addpublication_snapshot](assetId:///192b6214-df6e-44a3-bdd4-9d933a981619) at the Publisher on the publication database. Specify **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job_name** and **@job_password**. If the agent will use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher_security_mode** and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login information for **@publisher_login** and **@publisher_password**. This creates a Snapshot Agent job for the publication.  
  
3.  (Optional) Update the execution of [sp_addmergearticle](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c) to set any non-default values for parameters that implement new replication functionalities.  
  
### To upgrade scripts that add subscriptions to a merge publication  
  
1.  After executing the stored procedure that creates the subscription, ensure that you execute the stored procedure that creates a Merge Agent job to synchronize the subscription. The stored procedure that you use will depend on the type of subscription.  
  
    -   For a pull subscription, update the execution of [sp_addmergepullsubscription_agent](assetId:///a2f4b086-078d-49b5-8971-8a1e3f6a6feb) to supply the Windows credentials under which the Merge Agent runs at the Subscriber for **@job_name** and **@job_password**. This is done after the execution of [sp_addmergepullsubscription](assetId:///d63909a0-8ea7-4734-9ce8-8204d936a3e4). For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
    -   For a push subscription, execute [sp_addmergepushsubscription_agent](assetId:///808a1925-be46-4999-8d69-b3a83010ec81) at the Publisher. Specify **@subscriber**, **@subscriber_db**, **@publication**, the Windows credentials under which the Merge Agent at the Distributor runs for **@job_name** and **@job_password**, and a schedule for this agent job. For more information, see [Specify Synchronization Schedules](../../Topics/TopicNameNotContainA/Specify-Synchronization-Schedules.md). This is done after the execution of [sp_addmergesubscription](assetId:///a191d817-0132-49ff-93ca-76f13e609b38). For more information, see [Create a Push Subscription](../../Topics/TopicNameContainA/Create-a-Push-Subscription.md).  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/tokens/ssVersion2000_md.md)] script that creates a transactional publication for the Product table. This publication supports immediate updating with queued updating as failover. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createtranpub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpub_nwpreupgrade)]  
  
## Example  
 The following is an example of upgrading the previous script, which creates a transactional publication, to run successfully for [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] and later versions. This publication supports immediate updating with queued updating as failover. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createtranpub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/tokens/ssVersion2000_md.md)] script that creates a merge publication for the Customers table. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a merge publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createmergepub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/tokens/ssVersion2000_md.md)] script that creates a push subscription to a transactional publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createtranpushsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpushsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a push subscription to a transactional publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createtranpushsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpushsub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/tokens/ssVersion2000_md.md)] script that creates a push subscription to a merge publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepushsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepushsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a push subscription to a merge publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createmergepushsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepushsub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/tokens/ssVersion2000_md.md)] script that creates a pull subscription to a transactional publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepushsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepushsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a pull subscription to a transactional publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createtranpullsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpullsub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/tokens/ssVersion2000_md.md)] script that creates a pull subscription to a merge publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepullsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepullsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a pull subscription to a merge publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createmergepullsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepullsub_nwpostupgrade)]  
  
## See Also  
 [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md)   
 [Create a Push Subscription](../../Topics/TopicNameContainA/Create-a-Push-Subscription.md)   
 [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md)   
 [View and Modify Replication Security Settings](../../Topics/TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md)   
 [MSSQL_ENG021797](../../Topics/TopicNameNotContainA/MSSQL_ENG021797.md)   
 [MSSQL_ENG021798](../../Topics/TopicNameNotContainA/MSSQL_ENG021798.md)   
 [Programming Replication Using System Stored Procedures](assetId:///816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a)   
 [Upgrade Replicated Databases](../../Topics/TopicNameNotContainA/Upgrade-Replicated-Databases.md)