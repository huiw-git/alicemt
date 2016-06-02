---
title: Suspend an Availability Database (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86858982-6af1-4e80-9a93-87451f0d7ee9
---
# Suspend an Availability Database (SQL Server)
  You can suspend an availability database in [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. Note that a suspend command needs to be issued on the server instance that hosts the database to be suspended or resumed.  
  
 The effect of a suspend command depends on whether you suspend a secondary database or a primary database, as follows:  
  
|Suspended Database|Effect of Suspend Command|  
|------------------------|-------------------------------|  
|Secondary database|Only the local secondary database is suspended and its synchronization state becomes NOT SYNCHRONIZING. Other secondary databases are not affected. The suspended database stops receiving and applying data \(log records\) and begins to fall behind the primary database. Existing connections on the readable secondary remain usable. New connections to the suspended database on the readable secondary are not allowed until data movement is resumed.<br /><br /> The primary database remains available. If you suspend each of the corresponding secondary databases, the primary database runs exposed.<br /><br /> **\*\* Important \*\*** While a secondary database is suspended, the send queue of the corresponding primary database will accumulate unsent transaction log records. Connections to the secondary replica return data that was available at the time the data movement was suspended.|  
|Primary database|The primary database stops data movement to every connected secondary database. The primary database continues running, in an exposed mode. The primary database remains available to clients, and existing connections on a readable secondary remain usable and new connections can be made.|  
  
> [!NOTE]  
>  Suspending an Always On secondary database does not directly affect the availability of the primary database. However, suspending a secondary database can impact redundancy and failover capabilities for the primary database. This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database. Suspending an Always On primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Prerequisites](#Prerequisites)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To suspend a database, using:**  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Follow up:** [Avoiding a Full Transaction Log](#FollowUp)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 A SUSPEND command returns as soon as it has been accepted by the replica that hosts the target database, but actually suspending the database occurs asynchronously.  
  
###  <a name="Prerequisites"></a> Prerequisites  
 You must be connected to the server instance that hosts the database that you want to suspend. To suspend a primary database and the corresponding secondary databases, connect to the server instance that hosts the primary replica. To suspend a secondary database while leaving the primary database available, connect to the secondary replica.  
  
###  <a name="Recommendations"></a> Recommendations  
 During bottlenecks, suspending one or more secondary databases briefly might be useful to improve performance temporarily on the primary replica. As long as a secondary database remains suspended, the transaction log of the corresponding primary database cannot be truncated. This causes log records to accumulate on the primary database. Therefore, we recommend that you resume, or remove, a suspended secondary database quickly. For more information, see [Follow up: Avoiding a Full Transaction Log](#FollowUp), later in this topic.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To suspend a database**  
  
1.  In Object Explorer, connect to the server instance that hosts the availability replica on which you want to suspend a database, and expand the server tree. For more information, see [Prerequisites](#Prerequisites), earlier in this topic.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Expand the availability group.  
  
4.  Expand the **Availability Databases** node, right\-click the database, and click **Suspend Data Movement**.  
  
5.  In the **Suspend Data Movement** dialog box, click **OK**.  
  
     Object Explorer indicates that the database is suspended by changing  the database icon to display a pause indicator.  
  
> [!NOTE]  
>  To suspend additional databases on this replica location, repeat steps 4 and 5  for each database.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To suspend a database**  
  
1.  Connect to the server instance that hosts the replica whose database you want to suspend. For more information, see [Prerequisites](#Prerequisites), earlier in this topic.  
  
2.  Suspend the database by using the following [ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md)statement:  
  
     ALTER DATABASE *database\_name* SET HADR SUSPEND  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To suspend a database**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the replica whose database you want to suspend. For more information, see [Prerequisites](#Prerequisites), earlier in this topic.  
  
2.  Use the **Suspend\-SqlAvailabilityDatabase** cmdlet to suspend the availability group.  
  
     For example, the following command suspends data synchronization for the availability database `MyDb3` in the availability group `MyAg` on the server instance named `Computer\Instance`.  
  
    ```  
    Suspend-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="FollowUp"></a> Follow Up: Avoiding a Full Transaction Log  
 Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup. However, while a secondary database is suspended, all of the current log records remain active on the primary database. If the transaction log fills up \(either because it reaches its maximum size or the server instance runs out of space\), the database cannot perform any more updates.  
  
 To avoid this problem, you should do one of the following:  
  
-   Add more log space for the primary database.  
  
-   Resume the secondary database before the log fills up. For more information, see [Resume an Availability Database &#40;SQL Server&#41;](../Topic/Resume%20an%20Availability%20Database%20\(SQL%20Server\).md).  
  
-   Remove the secondary database. For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
 **To troubleshoot a full transaction log**  
  
-   [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../Topic/Troubleshoot%20a%20Full%20Transaction%20Log%20\(SQL%20Server%20Error%209002\).md)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Resume an Availability Database &#40;SQL Server&#41;](../Topic/Resume%20an%20Availability%20Database%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Resume an Availability Database &#40;SQL Server&#41;](../Topic/Resume%20an%20Availability%20Database%20\(SQL%20Server\).md)  
  
  