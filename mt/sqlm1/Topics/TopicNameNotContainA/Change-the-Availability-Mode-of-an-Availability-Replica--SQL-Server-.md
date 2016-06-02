---
title: Change the Availability Mode of an Availability Replica (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
---
# Change the Availability Mode of an Availability Replica (SQL Server)
  This topic describes how to change the availability mode of an availability replica in an Always On availability group in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell. The availability mode is a replica property that controls the whether the replica commits asynchronously or synchronously. *Asynchronous\-commit mode* maximizes performance at the expense of high availability and supports only forced manual failover \(with possible data loss\), typically called *forced failover*. *Synchronous\-commit mode* emphasizes high availability over performance and, once the secondary replica is synchronized, supports manual failover and, optionally, automatic failover.  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To change the availability mode of an availability replica, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must be connected to the server instance that hosts the primary replica.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To change the availability mode of an availability group**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Click the availability group whose replica you want to change.  
  
4.  Right\-click the replica, and click **Properties**.  
  
5.  In the **Availability Replica Properties** dialog box, use the **Availability mode** drop list to change the availability mode of this replica.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To change the availability mode of an availability group**  
  
1.  Connect to the server instance that hosts the primary replica.  
  
2.  Use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER AVAILABILITY GROUP *group\_name* MODIFY REPLICA ON '*server\_name*'  
  
     WITH \( {  
  
     AVAILABILITY\_MODE \= { SYNCHRONOUS\_COMMIT | ASYNCHRONOUS\_COMMIT }  
  
     | FAILOVER\_MODE \= { AUTOMATIC | MANUAL }  
  
     } \)  
  
     where *group\_name* is the name of the availability group and *server\_name* is the name of the server instance that hosts the replica to be modified.  
  
    > [!NOTE]  
    >  FAILOVER\_MODE \= AUTOMATIC is supported only if you also specify AVAILABILITY\_MODE \= SYNCHRONOUS\_COMMIT.  
  
     The following example, entered on the primary replica of the `AccountsAG` availability group, changes the availability and failover modes to synchronous commit and automatic failover, respectively, for the replica hosted by the `INSTANCE09` server instance.  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To change the availability mode of an availability group**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the primary replica.  
  
2.  Use the **Set\-SqlAvailabilityReplica** cmdlet with the **AvailabilityMode** parameter and, optionally, the **FailoverMode** parameter.  
  
     For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous\-commit availability mode and to support automatic failover.  
  
    ```  
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Availability Modes &#40;Always On Availability Groups&#41;](../Topic/Availability%20Modes%20\(Always%20On%20Availability%20Groups\).md)   
 [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../Topic/Failover%20and%20Failover%20Modes%20\(Always%20On%20Availability%20Groups\).md)  
  
  