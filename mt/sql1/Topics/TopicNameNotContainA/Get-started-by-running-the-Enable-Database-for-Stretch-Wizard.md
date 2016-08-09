---
title: "Get started by running the Enable Database for Stretch Wizard"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 855dd9fc-f80c-4dbc-bf46-55a9736bfe15
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Get started by running the Enable Database for Stretch Wizard
To configure a database for Stretch Database, run the Enable Database for Stretch Wizard.  This topic describes the info that you have to enter and the choices that you have to make in the wizard.  
  
 To learn more about Stretch Database, see [Stretch Database](../../Topics/TopicNameNotContainA/Stretch-Database.md).  
  
## Launch the wizard  
  
1.  In SQL Server Management Studio, in Object Explorer, select the database on which you want to enable Stretch.  
  
2.  Right-click and select **Tasks**, and then select **Stretch**, and then select **Enable** to launch the wizard.  
  
##  <a name="Intro"></a> Introduction  
 Review the purpose of the wizard and the prerequisites.  
  
 ![Introduction page of Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-1.png "Stretch)  
  
##  <a name="Tables"></a> Select tables  
 Select the tables that you want to enable for Stretch.  
  
 ![Select tables page of Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-2.png "Stretch)  
  
|Column|Description|  
|------------|-----------------|  
|(no title)|Check the check box in this column to enable the selected table for Stretch.|  
|**Name**|Specifies the name of the column in the table.|  
|(no title)|A symbol in this column typically indicates that you can't enable the selected table for Stretch because of a blocking issue. This may be because the table uses an unsupported data type. Hover over the symbol to display more info in a tooltip. For more info, see [Limitations for Stretch Database](../../Topics/TopicNameNotContainA/Limitations-for-Stretch-Database.md).|  
|**Stretched**|Indicates whether the table is already enabled.|  
|**Migrate**|In RC3, you can migrate an entire table (**Entire Table**) or you can specify a date-based filter predicate in the wizard. If you want to use a different filter predicate to select rows to migrate, run the ALTER TABLE statement to specify the filter predicate after you exit the wizard. For more info about the filter predicate, see [Select rows to migrate by using a filter predicate (Stretch Database)](../../Topics/TopicNameContainA/Select-rows-to-migrate-by-using-a-filter-predicate--Stretch-Database-.md). For more info about how to apply the predicate, see [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md) or [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1).|  
|**Rows**|Specifies the number of rows in the table.|  
|**Size (KB)**|Specifies the size of the table in KB.|  
  
## Optionally provide a date-based filter predicate  
 If you want to provide a date-based filter predicate to select rows to migrate, do the following things on the **Select tables** page.  
  
1.  In the **Select the tables you want to stretch** list, click **Entire Table** in the row for the table. The **Select rows to stretch** dialog box opens.  
  
     ![Define a date&#45;based filter predicate](../../Topics/TopicNameNotContainA/images/Stretch-wizard-2a.png "Stretch)  
  
2.  In the **Select rows to stretch** dialog box, select **Choose Rows**.  
  
3.  In the **Name field**, provide a name for the filter predicate.  
  
4.  For the **Where** clause, pick a date column from the table, pick an operator, and provide a date value.  
  
5.  Click **Check** to test the predicate. If the predicate returns results from the table - that is, if there are rows to migrate that satisfy the condition - the test reports **Success**.  
  
6.  Click Done to return to the **Select tables** page.  
  
     ![Select Tables page after defining a filter predicate](../../Topics/TopicNameNotContainA/images/Stretch-wizard-2b.png "Stretch)  
  
##  <a name="Configure"></a> Configure Azure  
  
1.  Sign in to Microsoft Azure with a Microsoft account.  
  
     ![Sign in to Azure &#45; Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-3.png "Stretch)  
  
2.  Select the Azure subscription to use for Stretch Database.  
  
3.  Select the Azure region to use for Stretch Database. If you create a new server, the server is created in this region.  
  
     To minimize latency, pick the Azure region in which your SQL Server is located. For more info about regions, see [Azure Regions](https://azure.microsoft.com/regions/).  
  
4.  Specify whether you want to use an existing server or create a new Azure server.  
  
     If the Active Directory on your SQL Server is federated with Azure Active Directory, you can optionally use a federated service account for SQL Server to communicate with the remote Azure server. For more info about the requirements for this option, see [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc).  
  
    -   **Create new server**  
  
        1.  Create a login and password for the server administrator.  
  
        2.  Optionally, use a federated service account for SQL Server to communicate with the remote Azure server.  
  
         ![Create new Azure server &#45; Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-4.png "Stretch)  
  
    -   **Existing server**  
  
        1.  Select or enter the name of the existing Azure server.  
  
        2.  Select the authentication method.  
  
            -   If you select **SQL Server Authentication**, create a new login and password.  
  
            -   Select **Active Directory Integrated Authentication** to use a federated service account for SQL Server to communicate with the remote Azure server.  
  
         ![Select existing Azure server &#45; Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-5.png "Stretch)  
  
##  <a name="Credentials"></a> Secure credentials  
 You have to have a database master key to secure the credentials that Stretch Database uses to connect to the remote database.  
  
 If a database master key already exists, enter the password for it.  
  
 ![Secure credentials page of the Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-6b.PNG "Stretch)  
  
 If the database does not have an existing master key, enter a strong password to create a database master key.  
  
 ![Secure credentials page of the Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-6.png "Stretch)  
  
 For more info about the database master key, see [CREATE MASTER KEY (Transact-SQL)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76) and [Create a Database Master Key](../../Topics/TopicNameContainA/Create-a-Database-Master-Key.md). For more info about the credential that the wizard creates,  see [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045).  
  
##  <a name="Network"></a> Select IP address  
 Use the public IP address of your SQL Server, or enter a range of IP addresses, to create a firewall rule on Azure that lets SQL Server communicate with the remote Azure server.  
  
 The IP address or addresses that you provide on this page tell the Azure server to allow incoming data, queries, and management operations initiated by SQL Server to pass through the Azure firewall. The wizard doesn't change anything in the firewall settings on the SQL Server.  
  
 ![Select IP address page of the Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-7.png "Stretch)  
  
##  <a name="Summary"></a> Summary  
 Review the values that you entered and the options that you selected in the wizard and the estimated costs on Azure. Then select **Finish** to enable Stretch.  
  
 ![Summary page of the Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-8.png "Stretch)  
  
##  <a name="Results"></a> Results  
 Review the results.  
  
 To monitor the status of data migration, see [Monitor and troubleshoot data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Monitor-and-troubleshoot-data-migration--Stretch-Database-.md).  
  
 ![Results page of the Stretch Database wizard](../../Topics/TopicNameNotContainA/images/Stretch-wizard-9.PNG "Stretch)  
  
##  <a name="KnownIssues"></a> Troubleshooting the wizard  
 **The Stretch Database wizard failed.**  
 If Stretch Database is not yet enabled at the server level, and you run the wizard without the system administrator permissions to enable it, the wizard fails. Ask the  system administrator to enable Stretch Database on the local server instance, and then run the wizard again. For more info, see [Prerequisite: Permission to enable Stretch Database on the server](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-database.md#EnableTSQLServer).  
  
## Next steps  
 Enable additional tables for Stretch Database. Monitor data migration and manage Stretch-enabled databases and tables.  
  
-   [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md) to enable additional tables.  
  
-   [Monitor and troubleshoot data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Monitor-and-troubleshoot-data-migration--Stretch-Database-.md) to see the status of data migration.  
  
-   [Pause and resume data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Pause-and-resume-data-migration--Stretch-Database-.md)  
  
-   [Manage and troubleshoot Stretch Database](../../Topics/TopicNameNotContainA/Manage-and-troubleshoot-Stretch-Database.md)  
  
-   [Backup Stretch-enabled databases (Stretch Database)](../../Topics/TopicNameNotContainA/Backup-Stretch-enabled-databases--Stretch-Database-.md)  
  
## See Also  
 [Enable Stretch Database for a database](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-database.md)   
 [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md)