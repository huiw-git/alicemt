---
title: Remove a Primary Database from an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d4ca31e-ddf0-44bf-be5e-a5da060bf096
---
# Remove a Primary Database from an Availability Group (SQL Server)
  This topic describes how to remove both the primary database and the corresponding secondary database\(s\) from an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   **Before you begin:**  
  
     [Prerequisites and Restrictions](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To remove an availability database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Follow Up:**  [After Removing an Availability Database from an Availability Group](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites and Restrictions  
  
-   This task is supported only on primary replicas. You must be connected to the server instance that hosts the primary replica.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To remove an availability database**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica of the database or databases to be removed, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Select the availability group, and expand the **Availability Databases** node.  
  
4.  This step depends on whether you want to remove multiple databases groups or only one database, as follows:  
  
    -   To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove. For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Object%20Explorer%20Details%20to%20Monitor%20Availability%20Groups%20\(SQL%20Server%20Management%20Studio\).md).  
  
    -   To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.  
  
5.  Right\-click the selected database or databases, and select **Remove Database from Availability Group** in the command menu.  
  
6.  In the **Remove Databases from Availability Group** dialog box, to remove all the listed databases, click **OK**. If you do not want to remove all them, click **Cancel**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To remove an availability database**  
  
1.  Connect to the server instance that hosts the primary replica.  
  
2.  Use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER AVAILABILITY GROUP *group\_name* REMOVE DATABASE *availability\_database\_name*  
  
     where *group\_name* is the name of the availability group and *database\_name* is the name of the database to be removed.  
  
     The following example removes a databases named `Db6` from the `MyAG` availability group.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG REMOVE DATABASE Db6;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To remove an availability database**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the primary replica.  
  
2.  Use the **Remove\-SqlAvailabilityDatabase** cmdlet, specifying the name of the availability database to be removed from the availability group. When you are connected to the server instance that hosts the primary replica, the primary database and its corresponding secondary databases are all removed from the availability group.  
  
     For example, the following command removes the availability database `MyDb9` from the availability group named `MyAg`. Because the command is executed on the server instance that hosts the primary replica, the primary database and all its corresponding secondary databases are removed from the availability group. Data synchronization will no longer occur for this database on any secondary replica.  
  
    ```  
    Remove-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\Sql\PrimaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb9  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="FollowUp"></a> Follow Up: After Removing an Availability Database from an Availability Group  
 Removing an availability database from its availability group ends data synchronization between the former primary database and the corresponding secondary databases. The former primary database remains online. Every corresponding secondary database is placed in the RESTORING state.  
  
 At this point there are alternative ways of dealing with a removed secondary database:  
  
-   If you no longer need a given secondary database, you can drop it.  
  
     For more information, see [Delete a Database](../../Topics\TopicNameContainA/Delete-a-Database.md).  
  
-   If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database. However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online. You must make sure that clients can access only one of them, typically the most recent primary database.  
  
     For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../Topic/Recover%20a%20Database%20Without%20Restoring%20Data%20\(Transact-SQL\).md).  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
  