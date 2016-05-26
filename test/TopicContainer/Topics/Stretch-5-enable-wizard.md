---
title: Stretch 5 enable wizard
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b1dfc81-0f74-4397-860c-f7e8a2f1d0f0
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Stretch 5 enable wizard
  To configure a database for Stretch Database, run the Enable Database for Stretch Wizard.  This topic describes the info that you have to enter and the choices that you have to make in the wizard.

 To learn more about Stretch Database, see [Stretch Database](assetId:///ce6db775-21a5-40bc-95a1-f560376d4ee2).

## Launch the wizard

1.  In SQL Server Management Studio, in Object Explorer, select the database on which you want to enable Stretch.

2.  Right\-click and select **Tasks**, and then select **Stretch**, and then select **Enable** to launch the wizard.

##  <a name="Intro"></a> Introduction
 Review the purpose of the wizard and the prerequisites.

##  <a name="Tables"></a> Select tables
 Select the tables that you want to enable for Stretch.

|Column|Description|
|------------|-----------------|
|\(no title\)|Check the check box in this column to enable the selected table for Stretch.|
|**Name**|Specifies the name of the column in the table.|
|\(no title\)|A symbol in this column typically indicates that you can't enable the selected table for Stretch because of a blocking issue. This may be because the table uses an unsupported data type. Hover over the symbol to display more info in a tooltip. For more info, see [Surface area limitations and blocking issues for Stretch Database](assetId:///2b1fbec1-7859-44fc-8417-724fc57a59c0).|
|**Stretched**|Indicates whether the table is already enabled.|
|**Rows**|Specifies the number of rows in the table.|
|**Size \(KB\)**|Specifies the size of the table in KB.|
|**Migrate**|In CTP 3.1 through RC0, you can only migrate an entire table by using the wizard. If you want to specify  a predicate to select rows to migrate from a table that contains both historical and current data, run the ALTER TABLE statement to specify a predicate after you exit the wizard. For more info, see [Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc) or [ALTER TABLE \(Transact\-SQL\)](assetId:///f1745145-182d-4301-a334-18f799d361d1).|

##  <a name="Configure"></a> Configure Azure deployment

1.  Sign in to Microsoft Azure with a Microsoft account.

2.  Select the Azure subscription to use for Stretch Database.

3.  Select an Azure region. If you create a new server, the server is created in this region.

     To minimize latency, pick the Azure region in which your SQL Server is located. For more info about regions, see [Azure Regions](https://azure.microsoft.com/regions/).

4.  Specify whether you want to use an existing server or create a new Azure server.

     If the Active Directory on your SQL Server is federated with Azure Active Directory, you can optionally use a federated service account for SQL Server to communicate with the remote Azure server. For more info about the requirements for this option, see [ALTER DATABASE SET Options \(Transact\-SQL\)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc).

    -   **Existing server**

        1.  Select or enter the name of the existing Azure server.

        2.  Select the authentication method.

            -   If you select **SQL Server Authentication**, create a new login and password.

            -   Select **Active Directory Integrated Authentication** to use a federated service account for SQL Server to communicate with the remote Azure server.

    -   **Create new server**

        1.  Create a login and password for the server administrator.

        2.  Optionally, use a federated service account for SQL Server to communicate with the remote Azure server.

##  <a name="Credentials"></a> Secure credentials
 Enter a strong password to create a database master key, or if a database master key already exists, enter the password for it.

 You have to have a database master key to secure the credentials that Stretch Database uses to connect to the remote database.

 For more info about the database master key, see [CREATE MASTER KEY \(Transact\-SQL\)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76) and [Create a Database Master Key](assetId:///8cb24263-e97d-4e4d-9429-6cf494a4d5eb). For more info about the credential that the wizard creates,  see [CREATE DATABASE SCOPED CREDENTIAL \(Transact\-SQL\)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045).

##  <a name="Network"></a> Select IP address
 Use the public IP address of your SQL Server, or enter a range of IP addresses, to create a firewall rule on Azure that lets SQL Server communicate with the remote Azure server.

##  <a name="Summary"></a> Summary
 Review the values that you entered and the options that you selected in the wizard. Then select **Finish** to enable Stretch.

##  <a name="Results"></a> Results
 Review the results.

 Optionally select **Monitor** to launch monitor the status of data migration in Stretch Database Monitor. For more info, see [Monitor and troubleshoot data migration \(Stretch Database\)](assetId:///06950858-8c02-4ec6-9c59-42b787316a2d).

##  <a name="KnownIssues"></a> Troubleshooting the wizard
 **The Stretch Database wizard failed.**
 If Stretch Database is not yet enabled at the server level, and you run the wizard without the system administrator permissions to enable it, the wizard fails. Ask the  system administrator to enable Stretch Database on the local server instance, and then run the wizard again. For more info, see [Prerequisite: Permission to enable Stretch Database on the server](assetId:///37854256-8c99-4566-a552-432e3ea7c6da#EnableTSQLServer).

## Next steps
 Enable additional tables for Stretch Database. Monitor data migration and manage Stretch\-enabled databases and tables.

-   [Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc) to enable additional tables.

-   [Monitor Stretch Database](assetId:///06950858-8c02-4ec6-9c59-42b787316a2d) to see the status of data migration.

-   [Pause and resume Stretch Database](assetId:///65d6a990-b295-41b2-97f9-7b6bf3000e4d)

-   [Manage and troubleshoot Stretch Database](assetId:///6334db3e-9297-44df-8d53-211187a95520)

-   [Backup and restore Stretch\-enabled databases](assetId:///18f0dff0-d8ce-4bee-a935-76ed6dfb3208)

## See Also
 [Enable Stretch Database for a database](assetId:///37854256-8c99-4566-a552-432e3ea7c6da) 
 [Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc)

  