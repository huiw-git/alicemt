---
title: Get started by running the Enable Database for Stretch Wizard
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 855dd9fc-f80c-4dbc-bf46-55a9736bfe15
---
# Get started by running the Enable Database for Stretch Wizard
 To configure a database for Stretch Database, run the Enable Database for Stretch Wizard.  This topic describes the info that you have to enter and the choices that you have to make in the wizard.  
  
 To learn more about Stretch Database, see [Stretch Database](../../Topics\TopicNameNotContainA/Stretch-Database.md).  
  
## Launch the wizard  
  
1.  In SQL Server Management Studio, in Object Explorer, select the database on which you want to enable Stretch.  
  
2.  Right\-click and select **Tasks**, and then select **Stretch**, and then select **Enable** to launch the wizard.  
  
##  <a name="Intro"></a> Introduction  
 Review the purpose of the wizard and the prerequisites.  
 
 The important prerequisites include the following.
 -   You have to be an administrator to change database settings.
 -   You have to have a Microsoft Azure subscription.
 -   Your SQL Server has to be able to communicate with the remote Azure server.
  
 ![Introduction page of Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-1.png "Stretch wizard 1")  
  
##  <a name="Tables"></a> Select tables  
 Select the tables that you want to enable for Stretch.  
 
Tables with lots of rows appear at the top of the sorted list. Before the Wizard displays the list of tables, it analyzes them for data types that are not currently supported by Stretch Database. 
  
 ![Select tables page of Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-2.png "Stretch wizard 2")  
  
|Column|Description|  
|------------|-----------------|  
|\(no title\)|Check the check box in this column to enable the selected table for Stretch.|  
|**Name**|Specifies the name of the table in the database.|  
|\(no title\)|A symbol in this column may represent a warning that doesn\'t prevent you from enabling the selected table for Stretch. It may also represent a blocking issue that prevents you from enabling the selected table for Stretch \- for example, because the table uses an unsupported data type. Hover over the symbol to display more info in a tooltip. For more info, see [Limitations for Stretch Database](../../Topics\TopicNameNotContainA/Limitations-for-Stretch-Database.md).|  
|**Stretched**|Indicates whether the table is already enabled for Stretch.|  
|**Migrate**|You can migrate an entire table \(**Entire Table**\) or you can specify a filter on an existing column in the table. If you want to use a different filter predicate to select rows to migrate, run the ALTER TABLE statement to specify the filter predicate after you exit the wizard. For more info about the filter predicate, see [Select rows to migrate by using a filter predicate](Select%20rows%20to%20migrate%20by%20using%20a%20filter%20predicate%20\(Stretch%20Database\).md). For more info about how to apply the predicate, see [Enable Stretch Database for a table](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-table.md) or [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md).|  
|**Rows**|Specifies the number of rows in the table.|  
|**Size \(KB\)**|Specifies the size of the table in KB.|  
  
## Optionally provide a row filter  
 If you want to provide a filter predicate to select rows to migrate, do the following things on the **Select tables** page.  
  
1.  In the **Select the tables you want to stretch** list, click **Entire Table** in the row for the table. The **Select rows to stretch** dialog box opens.  
  
     ![Define a date-based filter predicate](../../Images\Image\ImageContaina/Stretch-wizard-2a.png "Stretch wizard 2a")  
  
2.  In the **Select rows to stretch** dialog box, select **Choose Rows**.  
  
3.  In the **Name field**, provide a name for the filter predicate.  
  
4.  For the **Where** clause, pick a column from the table, pick an operator, and provide a value.  
  
5.  Click **Check** to test the predicate. If the predicate returns results from the table \- that is, if there are rows to migrate that satisfy the condition \- the test reports **Success**.  

    >   [!NOTE] The textbox that displays the filter query is read-only. You can't edit the query in the textbox.
  
6.  Click Done to return to the **Select tables** page.  

The filter function is created in SQL Server only when you finish the wizard. Until then, you can return to the **Select tables** page to change or rename the filter function.
  
     ![Select Tables page after defining a filter predicate](../../Images\Image\ImageContaina/Stretch-wizard-2b.png "Stretch wizard 2b")  
  
If you want to use a different type of filter predicate to select rows to migrate, do one of the following things.  
  
-   Exit the wizard and run the ALTER TABLE statement to enable Stretch for the table and to specify a predicate. For more info, see [Enable Stretch Database for a table](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-table.md).  
  
-   Run the ALTER TABLE statement to specify a predicate after you exit the wizard. For the required steps, see [Add a filter predicate after running the Wizard](Select%20rows%20to%20migrate%20by%20using%20a%20filter%20predicate%20\(Stretch%20Database\).md\#addafterwiz).  
  
##  <a name="Configure"></a> Configure Azure  
  
1.  Sign in to Microsoft Azure with a Microsoft account.  
  
     ![Sign in to Azure - Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-3.png "Stretch wizard 3")  
  
2.  Select the existing Azure subscription to use for Stretch Database.  
  
3.  Select the Azure region to use for Stretch Database.
    -   If you create a new server, the server is created in this region.  
    -   If you have existing servers in the selected region, the wizard lists them when you choose **Existing server**.
  
     To minimize latency, pick the Azure region in which your SQL Server is located. For more info about regions, see [Azure Regions](https://azure.microsoft.com/regions/).  
  
4.  Specify whether you want to use an existing server or create a new Azure server.  
  
     If the Active Directory on your SQL Server is federated with Azure Active Directory, you can optionally use a federated service account for SQL Server to communicate with the remote Azure server. For more info about the requirements for this option, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
    -   **Create new server**  
  
        1.  Create a login and password for the server administrator.  
  
        2.  Optionally, use a federated service account for SQL Server to communicate with the remote Azure server.  
  
         ![Create new Azure server - Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-4.png "Stretch wizard 4")  
  
    -   **Existing server**  
  
        1.  Select the existing Azure server.  
  
        2.  Select the authentication method.  
  
            -   If you select **SQL Server Authentication**, provide the administrator login and password.  
  
            -   Select **Active Directory Integrated Authentication** to use a federated service account for SQL Server to communicate with the remote Azure server. If the selected server is not integrated with Azure Active Directory, this option doesn't appear.
  
         ![Select existing Azure server - Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-5.png "Stretch wizard 5")  
  
##  <a name="Credentials"></a> Secure credentials  
 You have to have a database master key to secure the credentials that Stretch Database uses to connect to the remote database.  
  
 If a database master key already exists, enter the password for it.  
  
 ![Secure credentials page of the Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-6b.PNG "Stretch wizard 6b")  
  
 If the database does not have an existing master key, enter a strong password to create a database master key.  
  
 ![Secure credentials page of the Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-6.png "Stretch wizard 6")  
  
 For more info about the database master key, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20MASTER%20KEY%20\(Transact-SQL\).md) and [Create a Database Master Key](../../Topics\TopicNameContainA/Create-a-Database-Master-Key.md). For more info about the credential that the wizard creates,  see [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20SCOPED%20CREDENTIAL%20\(Transact-SQL\).md).  
  
##  <a name="Network"></a> Select IP address  
 Use the subnet IP address range (recommended), or the public IP address of your SQL Server, to create a firewall rule on Azure that lets SQL Server communicate with the remote Azure server.  
  
 The IP address or addresses that you provide on this page tell the Azure server to allow incoming data, queries, and management operations initiated by SQL Server to pass through the Azure firewall. The wizard doesn't change anything in the firewall settings on the SQL Server.  
  
 ![Select IP address page of the Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-7.png "Stretch wizard 7")  
  
##  <a name="Summary"></a> Summary  
 Review the values that you entered and the options that you selected in the wizard and the estimated costs on Azure. Then select **Finish** to enable Stretch.  
  
 ![Summary page of the Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-8.png "Stretch wizard 8")  
  
##  <a name="Results"></a> Results  
 Review the results.  
  
 To monitor the status of data migration, see [Monitor and troubleshoot data migration &#40;Stretch Database&#41;](../Topic/Monitor%20and%20troubleshoot%20data%20migration%20\(Stretch%20Database\).md).  
  
 ![Results page of the Stretch Database wizard](../../Images\Image\ImageNotContaina/Stretch-wizard-9.PNG "Stretch wizard 9")  
  
##  <a name="KnownIssues"></a> Troubleshooting the wizard  
 **The Stretch Database wizard failed.**  
 If Stretch Database is not yet enabled at the server level, and you run the wizard without the system administrator permissions to enable it, the wizard fails. Ask the  system administrator to enable Stretch Database on the local server instance, and then run the wizard again. For more info, see [Prerequisite: Permission to enable Stretch Database on the server](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-database.md).  
  
## Next steps  
 Enable additional tables for Stretch Database. Monitor data migration and manage Stretch\-enabled databases and tables.  
  
-   [Enable Stretch Database for a table](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-table.md) to enable additional tables.  
  
-   [Monitor and troubleshoot data migration &#40;Stretch Database&#41;](../Topic/Monitor%20and%20troubleshoot%20data%20migration%20\(Stretch%20Database\).md) to see the status of data migration.  
  
-   [Pause and resume data migration &#40;Stretch Database&#41;](../Topic/Pause%20and%20resume%20data%20migration%20\(Stretch%20Database\).md)  
  
-   [Manage and troubleshoot Stretch Database](../../Topics\TopicNameNotContainA/Manage-and-troubleshoot-Stretch-Database.md)  
  
-   [Backup Stretch-enabled databases](Backup%20Stretch-enabled%20databases%20\(Stretch%20Database\).md)  
  
-   [Restore Stretch-enabled databases](Restore%20Stretch-enabled%20databases%20\(Stretch%20Database\).md)  
  
## See Also  
 [Enable Stretch Database for a database](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-database.md)   
 [Enable Stretch Database for a table](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-table.md)  
  
  