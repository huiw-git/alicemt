---
title: "Create Table SQL Statement (SQL Server Import and Export Wizard)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
caps.latest.revision: 51
manager: jhubbard
---
# Create Table SQL Statement (SQL Server Import and Export Wizard)
In the **Column Mappings** dialog box, if you select **Create destination table** and then select **Edit SQL**, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard shows the **Create Table SQL Statement** dialog box. On this page, you can review and customize the CREATE TABLE command that the wizard will run to create the destination table.  
  
> [!NOTE]  
>  If you're looking for info about the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] CREATE TABLE statement, and not about this page of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard, see [CREATE TABLE (Transact-SQL)](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b).  
  
 For more info about how the wizard maps data types from source columns to destination columns, see [How the Wizard maps data types from source to destination](../../Topics/TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md#wizardMapping).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics/TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
> [!NOTE]  
>  If the **Create destination table** option and the **Edit SQL** button are disabled on the **Column Mappings** page, go back to the **Select Source Tables and Views** page and enter the name of a new table in the **Destination** column. After you specify a new destination table or tables and click **Next**, the **Create destination table** option is automatically selected and the **Edit SQL** button is enabled on the **Column Mappings** page. You can select **Edit SQL** to show the **Create Table SQL Statement** dialog box.  
  
## Screen shot  
 The following screen shot shows the **Create Table SQL Statement** dialog box of the Wizard.  
  
 ![Create table page of the Import and Export Wizard](../../Topics/TopicNameNotContainA/images/Create-table.png "Create)  
  
## Options on this page  
 **SQL statement**  
 Displays the auto-generated SQL statement and lets you customize it. For more info about the CREATE TABLE statement and syntax, see [CREATE TABLE (Transact-SQL)](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b).  
  
 If you change the default CREATE TABLE command, you may also have to make changes to the associated column mappings.  
  
 To include a carriage return in the text of the SQL statement, press CTRL+ENTER. If you press only ENTER, the dialog box closes.  
  
 **Autogenerate**  
 Restore the default SQL statement, if you have modified it, by clicking **Autogenerate**.  
  
## When the source table contains a FILESTREAM column  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard generates a default CREATE TABLE statement based on the connected data source. This default CREATE TABLE statement does not include the FILESTREAM attribute even if the source table has a FILESTREAM column. To copy a FILESTREAM column by using the wizard, first implement FILESTREAM storage on the destination database. Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box. For more info about FILESTREAM, see [Binary Large Object (Blob) Data (SQL Server)](../../Topics/TopicNameNotContainA/Binary-Large-Object--Blob--Data--SQL-Server-.md).  
  
## What's next?  
 After you review and customize the CREATE TABLE command and click **OK**, the **Create Table SQL Statement** dialog box returns you to the **Column Mappings** dialog box. For more info, see [Column Mappings (SQL Server Import and Export Wizard)](../../Topics/TopicNameNotContainA/Column-Mappings--SQL-Server-Import-and-Export-Wizard-.md).