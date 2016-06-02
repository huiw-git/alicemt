---
title: Join a Secondary Database to an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
---
# Join a Secondary Database to an Availability Group (SQL Server)
  This topic explains how to join a secondary database to an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. After you prepare a secondary database for a secondary replica, you need to join the database to the availability group as soon as possible. This will start data movement from the corresponding primary database to the secondary database.  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To prepare a secondary database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  For information about what happens after a secondary database joins the group, see [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must be connected to the server instance that hosts the secondary replica.  
  
-   The secondary replica must already be joined to the availability group. For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
-   The secondary database must have been prepared recently. For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To join a secondary database to an availability group**  
  
1.  In Object Explorer, connect to the server instance that hosts the secondary replica, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Expand the availability group that you want to change, and expand the **Availability Databases** node.  
  
4.  Right\-click the database, and click **Join to Availability Group**.  
  
5.  This opens the **Join Databases to Availability Group** dialog box. Verify the availability group name, which is displayed on the title bar, and database name or names displayed in the grid, and click **OK**, or click **Cancel**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To join a secondary database to an availability group**  
  
1.  Connect to the server instance that hosts the secondary replica.  
  
2.  Use the [SET HADR clause of the ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER DATABASE *database\_name* SET HADR AVAILABILITY GROUP \= *group\_name*  
  
     where *database\_name* is the name of a database to be joined and *group\_name* is the name of the availability group.  
  
     The following example joins the secondary database, `Db1`, to the local secondary replica of the `MyAG` availability group.  
  
    ```  
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  To see this [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](../Topic/Create%20an%20Availability%20Group%20\(Transact-SQL\).md).  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To join a secondary database to an availability group**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the secondary replica.  
  
2.  Use the **Add\-SqlAvailabilityDatabase** cmdlet to join one or more secondary databases to the availability group.  
  
     For example, the following command joins a secondary database, `Db1`, to the availability group `MyAG` on one of the server instances that hosts a secondary replica.  
  
    ```  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
## See Also  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Troubleshoot Always On Availability Groups Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Always%20On%20Availability%20Groups%20Configuration%20\(SQL%20Server\).md)  
  
  