---
title: Detaching and Attaching DQS Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
---
# Detaching and Attaching DQS Databases
  This topic describes how to detach and attach the DQS databases.  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Limitations"></a> Limitations and Restrictions  
 For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](../Topic/Database%20Detach%20and%20Attach%20\(SQL%20Server\).md).  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Ensure that there are no running activities or processes in DQS. This can be verified using the **Activity Monitoring** screen. For detailed information about working in this screen, see [Monitor DQS Activities](../../Topics\TopicNameNotContainA/Monitor-DQS-Activities.md).  
  
-   Ensure that there are no users logged on the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)].  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
  
-   Your Windows user account must be a member of the db\_owner fixed server role in the SQL Server instance to detach DQS databases.  
  
-   Your Windows user account must have CREATE DATABASE, CREATE ANY DATABASE, or ALTER ANY DATABASE permission to attach a database.  
  
-   You must have the dqs\_administrator role on the DQS\_MAIN database to terminate any running activities or stop any running processes in DQS.  
  
##  <a name="Detach"></a> Detach DQS Databases  
 When you detach a DQS database using SQL Server Management Studio, the detached files remain on your computer, and can be reattached to the same SQL Server instance or can be can be moved to another server and attached there. The DQS database files are typically available at the following location on your Data Quality Services computer: C:\\Program Files\\Microsoft SQL Server\\MSSQL13.*\<Instance\_Name\>*\\MSSQL\\DATA.  
  
1.  Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.  
  
2.  In Object Explorer, expand the **Databases** node.  
  
3.  Right\-click the **DQS\_MAIN** database, point to **Tasks**, and then click **Detach**. The **Detach Database** dialog box appears.  
  
4.  Select the check box under the **Drop** column, and click **OK** to detach the DQS\_MAIN database.  
  
5.  Repeat steps 3 and 4 with the DQS\_PROJECTS and DQS\_STAGING\_DATA databases to detach them.  
  
 You can also detach DQS databases using the Transact\-SQL statements by using the sp\_detach\_db stored procedure. For more information about detaching databases using Transact\-SQL statements, see [Using Transact\-SQL](../../Topics\TopicNameContainA/Detach-a-Database.md) in [Detach a Database](../../Topics\TopicNameContainA/Detach-a-Database.md).  
  
##  <a name="Attach"></a> Attach DQS Databases  
 Use the following instructions to attach a DQS database to the same SQL Server instance \(from where you detached\) or a different SQL Server instance where [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] is installed.  
  
1.  Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.  
  
2.  In Object Explorer, right\-click **Databases**, and then click **Attach**. The **Attach Databases** dialog box appears.  
  
3.  To specify the database to be attached, click **Add**. The **Locate Database Files** dialog box appears.  
  
4.  Select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database. For example, for the DQS\_MAIN database:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.  The **database details** \(lower\) pane displays the names of the files to be attached. To verify or change the pathname of a file, click the **Browse** button \(…\).  
  
6.  Click **OK** to attach the DQS\_MAIN database.  
  
7.  Repeat steps 2\-6 for the DQS\_PROJECTS and DQS\_STAGING\_DATA databases to attach them.  
  
8.  You must also run the Transact\-SQL statements in the next step after restoring the DQS\_MAIN database otherwise an error message is displayed when you try to connect to Data Quality Server by using the Data Quality Client application, and you cannot connect. However, you do not need to perform steps 9 and 10 if you have just attached the DQS\_PROJECTS or DQS\_STAGING\_DATA database, and not DQS\_MAIN.  
  
     To run the Transact\-SQL statements, in Object Explorer, right\-click the server, and then click **New Query**.  
  
9. In the Query Editor window, copy the following SQL statements:  
  
    ```  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
  
    ```  
  
10. Press F5 to execute the statements. Check the Results pane to verify that the statements have executed successfully. You will see the following message: `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`  
  
11. Connect to the Data Quality Server using the Data Quality Client to verify if you can connect successfully.  
  
 You can also attach DQS databases using the Transact\-SQL statements. For more information about attaching databases using Transact\-SQL statements, see [Using Transact-SQL](../../Topics\TopicNameContainA/Attach-a-Database.md) in [Attach a Database](../../Topics\TopicNameContainA/Attach-a-Database.md).  
  
## See Also  
 [Manage DQS Databases](../../Topics\TopicNameNotContainA/Manage-DQS-Databases.md)  
  
  