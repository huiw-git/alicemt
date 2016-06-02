---
title: Resume an Availability Database (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
---
# Resume an Availability Database (SQL Server)
  You can resume a suspended availability database in [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. Resuming a suspended database puts the database into the SYNCHRONIZING state. Resuming the primary database also resumes any of its secondary databases that were suspended as the result of suspending the primary database. If any secondary database was suspended locally, from the server instance that hosts the secondary replica, that secondary database must be resumed locally. Once a given secondary database and the corresponding primary database are in the SYNCHRONIZING state, data synchronization resumes on the secondary database.  
  
> [!NOTE]  
>  Suspending and resuming an Always On secondary database does not directly affect the availability of the primary database. However, suspending a secondary database can impact redundancy and failover capabilities for the primary database, until the suspended secondary database is resumed. This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database until mirroring is resumed. Suspending an Always On primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To resume a secondary database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
### Limitations and Restrictions  
 A RESUME command returns as soon as it has been accepted by the replica that hosts the target database, but actually resuming the database occurs asynchronously.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must be connected to the server instance that hosts the database to be resumed.  
  
-   The availability group must be online.  
  
-   The primary database must be online and available.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To resume a secondary database**  
  
1.  In Object Explorer, connect to the server instance that hosts the availability replica on which you want to resume a database, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Expand the availability group.  
  
4.  Expand the **Availability Databases** node, right\-click the database, and click **Resume Data Movement**.  
  
5.  In the **Resume Data Movement** dialog box, click **OK**.  
  
> [!NOTE]  
>  To resume additional databases on this replica location, repeat steps 4 and 5 for each database.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To resume a secondary database that was suspended locally**  
  
1.  Connect to the server instance that hosts the secondary replica whose database you want to resume.  
  
2.  Resume the secondary database by using the following [ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md)statement:  
  
     ALTER DATABASE *database\_name* SET HADR RESUME  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To resume a secondary database**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the replica whose database you want to resume. For more information, see [Prerequisites](#Prerequisites), earlier in this topic.  
  
2.  Use the **Resume\-SqlAvailabilityDatabase** cmdlet to resume the availability group.  
  
     For example, the following command resumes data synchronization for the availability database `MyDb3` in the availability group `MyAg`.  
  
    ```  
    Resume-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Suspend an Availability Database &#40;SQL Server&#41;](../Topic/Suspend%20an%20Availability%20Database%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  