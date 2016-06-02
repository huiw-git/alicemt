---
title: Upgrade Replication Scripts (Replication Transact-SQL Programming)
ms.custom: na
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
---
# Upgrade Replication Scripts (Replication Transact-SQL Programming)
  [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script files can be used to programmatically configure a replication topology. For more information, see [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md).  
  
> [!IMPORTANT]  
>  Although you are not required to upgrade scripts that are executed by members of the **sysadmin** role, we recommend that you modify existing scripts as described in this topic. Specify an account that has minimum permissions for each replication agent as described in the "Permissions Required By Agents" section of the topic [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
 These security improvements, which enable more control over permissions by allowing you to explicitly specify the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows accounts under which replication agent jobs are executed, affect the following stored procedures in existing scripts:  
  
-   **sp\_addpublication\_snapshot**:  
  
     You should now supply the Windows credentials as **@job\_login** and **@job\_password** when executing [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md) to create the job under which the Snapshot Agent runs at the Distributor.  
  
-   **sp\_addpushsubscription\_agent**:  
  
     You should now execute [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpushsubscription_agent%20\(Transact-SQL\).md) to explicitly add a job and supply the Windows credentials \(**@job\_login** and **@job\_password**\) under which the Distribution Agent job runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], this was done automatically when a push subscription was created.  
  
-   **sp\_addmergepushsubscription\_agent**:  
  
     You should now execute [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addmergepushsubscription_agent%20\(Transact-SQL\).md) to explicitly add a job and supply the Windows credentials \(**@job\_login** and **@job\_password**\) under which the Merge Agent job runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], this was done automatically when a push subscription was created.  
  
-   **sp\_addpullsubscription\_agent**:  
  
     You should now supply the Windows credentials as **@job\_login** and **@job\_password** when executing [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpullsubscription_agent%20\(Transact-SQL\).md) to create the job under which the Distribution Agent runs at the Subscriber.  
  
-   **sp\_addmergepullsubscription\_agent**:  
  
     You should now supply the Windows credentials as **@job\_login** and **@job\_password** when executing [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md) to create the job under which the Merge Agent runs at the Subscriber.  
  
-   **sp\_addlogreader\_agent**:  
  
     You should now execute [sp_addlogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addlogreader_agent%20\(Transact-SQL\).md) to manually add the job and supply the Windows credentials under which the Log Reader Agent runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], this was done automatically when a transactional publication was created.  
  
-   **sp\_addqreader\_agent**:  
  
     You should now execute [sp_addqreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addqreader_agent%20\(Transact-SQL\).md) to manually add the job and supply the Windows credentials under which the Queue Reader Agent runs at the Distributor. In versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], this was done automatically when a transactional publication that supported queued updating was created.  
  
 In the security model introduced in [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], replication agents always make connections to the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] with Windows Authentication using the credentials supplied in **@job\_name** and **@job\_password**. For information about the requirements of Windows accounts used when running replication agent jobs, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
> [!IMPORTANT]  
>  When possible, prompt users to enter security credentials at runtime. If you store credentials in a script file, ensure that the file itself is secured.  
  
### To upgrade scripts that configure a snapshot or transactional publication  
  
1.  In the existing script, before [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md), execute [sp_addlogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addlogreader_agent%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify the Windows credentials under which the Log Reader Agent runs for **@job\_name** and **@job\_password**. If the agent will use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Log Reader Agent job for the publication database.  
  
    > [!NOTE]  
    >  This step is only for transactional publications and is not required for snapshot publications.  
  
2.  \(Optional\) Before [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md), execute [sp_addqreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addqreader_agent%20\(Transact-SQL\).md) at the Distributor on the distribution database. Specify the Windows credentials under which the Queue Reader Agent runs for **@job\_name** and **@job\_password**. This creates a Queue Reader Agent job for the Distributor.  
  
    > [!NOTE]  
    >  This step is only required for transactional publications that support queued updating subscribers.  
  
3.  \(Optional\) Update the execution of [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md) to set any non\-default values for parameters that implement new replication functionalities.  
  
4.  After [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md), execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job\_name** and **@job\_password**. If the agent will use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication.  
  
5.  \(Optional\) Update the execution of [sp_addarticle &#40;Transact-SQL&#41;](../Topic/sp_addarticle%20\(Transact-SQL\).md) to set any non\-default values for parameters that implement new replication functionalities.  
  
### To upgrade scripts that add subscriptions to a snapshot or transactional publication  
  
1.  After executing the stored procedure that creates the subscription, ensure that you execute the stored procedure that creates a Distribution Agent job to synchronize the subscription. The stored procedure that you use will depend on the type of subscription.  
  
    -   For a pull subscription, update the execution of [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpullsubscription_agent%20\(Transact-SQL\).md) to supply the Windows credentials under which the Distribution Agent runs at the Subscriber for **@job\_name** and **@job\_password**. This is done after the execution of [sp\_addpullsubscription](../Topic/sp_addpullsubscription%20\(Transact-SQL\).md). For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
    -   For a push subscription, execute [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpushsubscription_agent%20\(Transact-SQL\).md) at the Publisher. Specify **@subscriber**, **@subscriber\_db**, **@publication**, Windows credentials under which the Distribution Agent runs at the Distributor for **@job\_name** and **@job\_password**, and a schedule for this agent job. For more information, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md). This is done after the execution of [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md). For more information, see [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md).  
  
### To upgrade scripts that configure a merge publication  
  
1.  \(Optional\) In the existing script, update the execution of [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md) to set any non\-default values for parameters that implement new replication functionalities.  
  
2.  After [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md), execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job\_name** and **@job\_password**. If the agent will use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication.  
  
3.  \(Optional\) Update the execution of [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) to set any non\-default values for parameters that implement new replication functionalities.  
  
### To upgrade scripts that add subscriptions to a merge publication  
  
1.  After executing the stored procedure that creates the subscription, ensure that you execute the stored procedure that creates a Merge Agent job to synchronize the subscription. The stored procedure that you use will depend on the type of subscription.  
  
    -   For a pull subscription, update the execution of [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md) to supply the Windows credentials under which the Merge Agent runs at the Subscriber for **@job\_name** and **@job\_password**. This is done after the execution of [sp\_addmergepullsubscription](../Topic/sp_addmergepullsubscription%20\(Transact-SQL\).md). For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
    -   For a push subscription, execute [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addmergepushsubscription_agent%20\(Transact-SQL\).md) at the Publisher. Specify **@subscriber**, **@subscriber\_db**, **@publication**, the Windows credentials under which the Merge Agent at the Distributor runs for **@job\_name** and **@job\_password**, and a schedule for this agent job. For more information, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md). This is done after the execution of [sp\_addmergesubscription](../Topic/sp_addmergesubscription%20\(Transact-SQL\).md). For more information, see [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md).  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] script that creates a transactional publication for the Product table. This publication supports immediate updating with queued updating as failover. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createtranpub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpub_nwpreupgrade)]  
  
## Example  
 The following is an example of upgrading the previous script, which creates a transactional publication, to run successfully for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. This publication supports immediate updating with queued updating as failover. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createtranpub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] script that creates a merge publication for the Customers table. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a merge publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createmergepub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] script that creates a push subscription to a transactional publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createtranpushsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpushsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a push subscription to a transactional publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createtranpushsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpushsub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] script that creates a push subscription to a merge publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepushsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepushsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a push subscription to a merge publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createmergepushsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepushsub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] script that creates a pull subscription to a transactional publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepushsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepushsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a pull subscription to a transactional publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createtranpullsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createtranpullsub_nwpostupgrade)]  
  
## Example  
 The following is an example of a [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] script that creates a pull subscription to a merge publication. Default parameters have been removed for readability.  
  
 [!CODE [HowTo#sp_createmergepullsub_NWpreupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepullsub_nwpreupgrade)]  
  
## Example  
 The following is an example of the previous script, which creates a pull subscription to a merge publication, upgraded to run successfully for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. Defaults for new parameters have been explicitly declared.  
  
> [!NOTE]  
>  Windows credentials are supplied at runtime using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_createmergepullsub_NWpostupgrade](../CodeSnippet/SQL15/replication/howto#sp_createmergepullsub_nwpostupgrade)]  
  
## See Also  
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md)   
 [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md)   
 [View and Modify Replication Security Settings](../../Topics\TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md)   
 [MSSQL_ENG021797](../../Topics\TopicNameNotContainA/MSSQL_ENG021797.md)   
 [MSSQL_ENG021798](../../Topics\TopicNameNotContainA/MSSQL_ENG021798.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Upgrade Replicated Databases](../../Topics\TopicNameNotContainA/Upgrade-Replicated-Databases.md)  
  
  