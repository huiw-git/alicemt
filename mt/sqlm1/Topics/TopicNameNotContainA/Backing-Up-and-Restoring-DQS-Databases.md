---
title: Backing Up and Restoring DQS Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
---
# Backing Up and Restoring DQS Databases
  This topic describes how to back up and restore the DQS databases.  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must know or remember the password for the database master key that that you provided during the DQS server installation.  
  
-   Ensure that there are no running activities or processes in DQS. This can be verified using the **Activity Monitoring** screen. For detailed information about working in this screen, see [Monitor DQS Activities](../../Topics\TopicNameNotContainA/Monitor-DQS-Activities.md).  
  
-   Ensure that there are no users logged on the DQS server.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
  
-   Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to perform the backup and restore operations.  
  
-   You must have the dqs\_administrator role on the DQS\_MAIN database to terminate any running activities or stop any running processes in DQS.  
  
##  <a name="BackupRestore"></a> Backup and Restore DQS Databases  
  
1.  Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.  
  
2.  In Object Explorer, expand the **Databases** node.  
  
3.  Back up the DQS\_STAGING\_DATA database. For step\-by\-step instructions for backing a SQL Server database, see [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md).  
  
4.  Back up the DQS\_PROJECTS database.  
  
5.  Back up the DQS\_MAIN database.  
  
6.  Disconnect from the current instance of SQL Server, and connect to the SQL Server instance where you want to restore these databases.  
  
7.  Restore DQS\_MAIN database. For step\-by\-step instructions to restore a SQL Server database, see [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md).  
  
8.  Restore the DQS\_PROJECTS database.  
  
9. Restore the DQS\_STAGING\_DATA database.  
  
10. In Object Explorer, right\-click the server, and then click **New Query**.  
  
11. In the Query Editor window, copy the following SQL statements, and replace *\<PASSWORD\>* with the password that you provided during the DQS installation for the database master key:  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. Press F5 to execute the statements. Check the **Results** pane to verify that the statements have executed successfully.  
  
## See Also  
 [Manage DQS Databases](../../Topics\TopicNameNotContainA/Manage-DQS-Databases.md)  
  
  