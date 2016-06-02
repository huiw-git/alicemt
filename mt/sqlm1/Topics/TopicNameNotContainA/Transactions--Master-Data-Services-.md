---
title: Transactions (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
---
# Transactions (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], a transaction is recorded each time action is taken on a member. Transactions can be viewed by all users and reversed by administrators. Transactions show the date, time, and user who took the action, along with other details. Users can add an annotation to a transaction, to indicate why a transaction took place.  
  
## When Transaction Are Recorded  
 Transactions are recorded when members:  
  
-   Are created, deleted, or reactivated.  
  
-   Have attribute values changed.  
  
-   Are moved in a hierarchy.  
  
 Transactions are not recorded when business rules change attribute values.  
  
## View and Manage Transactions  
 In the **Explorer** functional area, you can view and annotate \(add comments to\) the transactions that you made yourself.  
  
 In the **Version Management** functional area, administrators can view all transactions for all users for the models they have access to, and reverse any of these transactions.  
  
 You can configure how long transaction log data is retained by setting the **Log retention in Days** property in system settings for the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, and by setting **Log Retention Days** when you create or edit a model. For more information, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md) and [Create a Model &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20\(Master%20Data%20Services\).md).  
  
 The SQL Server Agent job, MDS\_MDM\_Sample\_Log\_Maintenace, triggers cleanup of the transaction logs and runs every night. You can use SQL Server Agent to modify the schedule for this job.  
  
 You can also call the following stored procedures to clean the transaction logs.  
  
|Stored Procedure|Description|  
|----------------------|-----------------|  
|mdm.udpTransactionsCleanup|Cleans transaction history|  
|mdm.udpValidationsCleanup|Cleans validation History|  
|mdm.udpEntityStagingBatchTableCleanup|Cleans staging table|  
  
 **Sample**  
  
```  
DECLARE @CleanupOlderThanDate date = '2014-11-11',  
@ModelID INT = 7  
--Clean up Transaction Logs  
EXEC mdm.udpTransactionsCleanup @ModelID, @CleanupOlderThanDate;  
  
--Clean up Validation History  
EXEC mdm.udpValidationsCleanup @ModelID, @CleanupOlderThanDate;  
  
--Clean up EBS tables  
EXEC mdm.udpEntityStagingBatchTableCleanup @ModelID, @CleanupOlderThanDate;  
  
```  
  
## System Settings  
 There is a setting in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] that affects whether or not transactions are recorded when records are staged. You can adjust this setting in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. For more information, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md).  
  
 When importing data in this version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can specify whether or not to log transactions when initiating the stored procedure. For more information, see [Staging Stored Procedure &#40;Master Data Services&#41;](../Topic/Staging%20Stored%20Procedure%20\(Master%20Data%20Services\).md).  
  
## Concurrency  
 If a particular entity value is shown simultaneously in more than one Explorer session, concurrent edits to the same value are possible. Concurrent edits will not be detected automatically by MDS. This can occur when multiple users use the MDS Explorer in the Web browser from multiple sessions, for example from multiple computers, multiple browser tabs or windows, or multiple user accounts.  
  
 More than one user can update the same entity values without error despite transactions being enabled. Typically the last edit to the value in a sequence of time will take precedence. The duplicate edit conflict can be manually observed in the transaction history and can be reversed manually by the administrator. The transaction history will show the individual transactions for the **Prior value** and **New value** for the attribute in question from each session, but will not automatically resolve the conflict when multiple **New Values** exist for the same old value.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Undo an action by reversing a transaction \(administrators only\).|[Reverse a Transaction &#40;Master Data Services&#41;](../Topic/Reverse%20a%20Transaction%20\(Master%20Data%20Services\).md)|  
  
## External Resources  
 Blog post, [Transactions, Validation Issue and Staging table cleanup](http://go.microsoft.com/fwlink/p/?LinkId=615374), on msdn.com.  
  
## Related Content  
  
-   [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md)  
  
-   [Annotations &#40;Master Data Services&#41;](../Topic/Annotations%20\(Master%20Data%20Services\).md)  
  
  