---
title: Outdated Backup
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
---
# Outdated Backup
  This rule checks that a database has recent backups. Scheduling regular backups is important for protecting your databases against data loss from many different failures. The appropriate frequency for backing up data depends on the recovery model of the database, on business requirements about potential data loss, and on how frequently the database is updated. In a frequently updated database, the work-loss exposure increases fairly quickly between backups.  
  
## Best Practices Recommendations  
 We recommend that you perform backups frequently enough to protect databases against data loss.  
  
 The simple recovery model and full recovery model both require data backups. For either recovery model, you can supplement your full backups with differential backups to efficiently reduce the risk of data loss.  
  
 For a database that uses the full recovery model, we recommend that you take frequent log backups. For a production database that contains very important data, log backups would typically be taken every one to fifteen minutes.  
  
> [!NOTE]  
>  The recommended method for scheduling backups is a database maintenance plan.  
  
## For More Information  
 [Back Up and Restore of System Databases &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-System-Databases--SQL-Server-.md)  
  
 [Recovery Models &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md)  
  
 [Create a Differential Database Backup &#40;SQL Server&#41;](../../Topics/TopicNameContainA/Create-a-Differential-Database-Backup--SQL-Server-.md)  
  
 [Create a Full Database Backup &#40;SQL Server&#41;](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md)  
  
 [Maintenance Plans](../../Topics/TopicNameNotContainA/Maintenance-Plans.md)  
  
 [Transaction Log Backups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Transaction-Log-Backups--SQL-Server-.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  