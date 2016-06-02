---
title: Use the Add Database to Availability Group Wizard (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81e5e36d-735d-4731-8017-2654673abb88
---
# Use the Add Database to Availability Group Wizard (SQL Server Management Studio)
  Use the Add Database to Availability Group Wizard to help you add one or more databases to an existing Always On availability group.  
  
> [!NOTE]  
>  For information about using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] or PowerShell to add a database, see [Add a Database to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
 **In This Topic:**  
  
-   **Before you begin:**  
  
     [Prerequisites and Restrictions](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To add a database, using:**  [Add Database to Availability Group Wizard \(SQL Server Management Studio\)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 If you have never added a database to an availability group, see the "Availability Databases" section in [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
###  <a name="Prerequisites"></a> Prerequisites, Restrictions, and Recommendations  
  
-   You must be connected to the server instance that hosts the current primary replica.  
  
-   **Prerequisites for using full initial data synchronization**  
  
    -   All the database\-file paths must be identical on every server instance that hosts a replica for the availability group.  
  
    -   No primary database name can exist on any server instance that hosts a secondary replica. This means that none of the new secondary databases can exist yet.  
  
    -   You will need to specify a network share in order for the wizard to create and access backups. For the primary replica, the account used to start the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] must have read and write file\-system permissions on a network share. For secondary replicas, the account must have read permission on the network share.  
  
     If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually. You can do this before or after running the wizard. For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using the Add Database to Availability Group Wizard \(SQL Server Management Studio\)  
 **To Use the Add Database to Availability Group Wizard**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Right\-click the availability group to which you are adding a database, and select the **Add Database** command. This command launches the Add Database to Availability Group Wizard.  
  
4.  On the **Select Databases** page, select one or more databases. For more information, see [Select Databases Page &#40;New Availability Group Wizard and Add Database Wizard&#41;](../Topic/Select%20Databases%20Page%20\(New%20Availability%20Group%20Wizard%20and%20Add%20Database%20Wizard\).md).  
  
     If the database contains a database master key, enter the password for the database master key in the **Password** column.  
  
5.  On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group. Choose one of the following options:  
  
    -   **Full**  
  
         Select this option if your environment meets the requirements for automatically starting initial data synchronization \(for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic\).  
  
         If you select **Full**, after creating the availability group, the wizard will attempt to back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica. The wizard will then join every secondary database to the availability group.  
  
         In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read\-write access. The log backups will be part of your log backup chain. Store the log backup files appropriately.  
  
        > [!IMPORTANT]  
        >  For information about the required file\-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.  
  
    -   **Join only**  
  
         If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option. The wizard will join the existing secondary databases to the availability group.  
  
    -   **Skip initial data synchronization**  
  
         Select this option if you want to use your own database and log backups of your primary databases. For more information, see [Start Data Movement on an Always On Secondary Database &#40;SQL Server&#41;](../Topic/Start%20Data%20Movement%20on%20an%20Always%20On%20Secondary%20Database%20\(SQL%20Server\).md).  
  
     For more information, see [Select Initial Data Synchronization Page &#40;Always On Availability Group Wizards&#41;](../Topic/Select%20Initial%20Data%20Synchronization%20Page%20\(Always%20On%20Availability%20Group%20Wizards\).md).  
  
6.  On the **Connect to Existing Secondary Replicas** page, if the instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that host the availability replicas for this availability group are all running as a service in the same user account, click **Connect all**. If any of the server instances are running as a service under different accounts, click the individual **Connect** button to the right of each server instance name.  
  
     For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard: Add Databases Wizard&#41;](../Topic/Connect%20to%20Existing%20Secondary%20Replicas%20Page%20\(Add%20Replica%20Wizard:%20Add%20Databases%20Wizard\).md).  
  
7.  The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard. To make a change, you can click **Previous** to return to an earlier wizard page to change one or more values. The click **Next** to return to the **Validation** page, and click **Re\-run Validation**.  
  
     For more information, see [Validation Page &#40;Always On Availability Group Wizards&#41;](../Topic/Validation%20Page%20\(Always%20On%20Availability%20Group%20Wizards\).md).  
  
8.  On the **Summary** page, review your choices for the new availability group. To make a change, click **Previous** to return to the relevant page. After making the change, click **Next** to return to the **Summary** page.  
  
     For more information, see [Summary Page &#40;Always On Availability Group Wizards&#41;](../Topic/Summary%20Page%20\(Always%20On%20Availability%20Group%20Wizards\).md).  
  
     If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute. Then, to create and configure the new availability group, click **Finish**.  
  
9. The **Progress** page displays the progress of the steps for creating the availability group \(configuring endpoints, creating the availability group, and joining the secondary replica to the group\).  
  
     For more information, see [Progress Page &#40;Always On Availability Group Wizards&#41;](../Topic/Progress%20Page%20\(Always%20On%20Availability%20Group%20Wizards\).md).  
  
10. When these steps complete, the **Results** page displays the result of each step. If all these steps succeed, the new availability group is completely configured. If any of the steps result in an error, you might need to manually complete the configuration. For information about the cause of a given error, click the associated "Error" link in the **Result** column.  
  
     When the wizard completes, click **Close** to exit.  
  
     For more information, see [Results Page &#40;Always On Availability Group Wizards&#41;](../Topic/Results%20Page%20\(Always%20On%20Availability%20Group%20Wizards\).md).  
  
11. If initial data synchronization was not automatically started on all of you secondary database, you need to configure any not\-yet\-joined secondary databases. For more information, see [Start Data Movement on an Always On Secondary Database &#40;SQL Server&#41;](../Topic/Start%20Data%20Movement%20on%20an%20Always%20On%20Secondary%20Database%20\(SQL%20Server\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Add a Database to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)   
 [Start Data Movement on an Always On Secondary Database &#40;SQL Server&#41;](../Topic/Start%20Data%20Movement%20on%20an%20Always%20On%20Secondary%20Database%20\(SQL%20Server\).md)   
 [Add a Database to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
  