---
title: Configure the Transaction Set Job for an Oracle Publisher (Replication Transact-SQL Programming)
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
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
---
# Configure the Transaction Set Job for an Oracle Publisher (Replication Transact-SQL Programming)
  The **Xactset** job is an Oracle database job created by replication that runs at an Oracle Publisher to create transaction sets when the Log Reader Agent is not connected to the Publisher. You can enable and configure this job from the Distributor programmatically using replication stored procedures. For more information, see [Performance Tuning for Oracle Publishers](../../Topics\TopicNameNotContainA/Performance-Tuning-for-Oracle-Publishers.md).  
  
### To enable the transaction set job  
  
1.  At the Oracle Publisher, set the **job\_queue\_processes** initialization parameter to a sufficient value to allow the Xactset job run. For more information about this parameter, see the database documentation for the Oracle Publisher.  
  
2.  At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](../Topic/sp_publisherproperty%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**, a value of **xactsetbatching** for **@propertyname**, and a value of **enabled** for **@propertyvalue**.  
  
3.  At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](../Topic/sp_publisherproperty%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**, a value of **xactsetjobinterval** for **@propertyname**, and the job interval, in minutes, for **@propertyvalue**.  
  
4.  At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](../Topic/sp_publisherproperty%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**, a value of **xactsetjob** for **@propertyname**, and a value of **enabled** for **@propertyvalue**.  
  
### To configure the transaction set job  
  
1.  \(Optional\) At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](../Topic/sp_publisherproperty%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**. This returns properties of the **Xactset** job at the Publisher.  
  
2.  At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](../Topic/sp_publisherproperty%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**, the name of the Xactset job property being set for **@propertyname**, and new setting for **@propertyvalue**.  
  
3.  \(Optional\) Repeat step 2 for each Xactset job property being set. When changing the **xactsetjobinterval** property, you must restart the job on the Oracle Publisher for the new interval to take effect.  
  
### To view properties of the transaction set job  
  
1.  At the Distributor, execute [sp\_helpxactsetjob](../Topic/sp_helpxactsetjob%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**.  
  
### To disable the transaction set job  
  
1.  At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](../Topic/sp_publisherproperty%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**, a value of **xactsetjob** for **@propertyname**, and a value of **disabled** for **@propertyvalue**.  
  
## Example  
 The following example enables the `Xactset` job and sets an interval of three minutes between runs.  
  
 [!CODE [HowTo#sp_enable_xactsetjob](../CodeSnippet/SQL15/replication/howto#sp_enable_xactsetjob)]  
  
## See Also  
 [Performance Tuning for Oracle Publishers](../../Topics\TopicNameNotContainA/Performance-Tuning-for-Oracle-Publishers.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)  
  
  