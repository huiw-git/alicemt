---
title: Create Table SQL Statement (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
---
# Create Table SQL Statement (SQL Server Import and Export Wizard)
  In the **Column Mappings** dialog box, if you select **Create destination table** and then select **Edit SQL**, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows the **Create Table SQL Statement** dialog box. On this page, you can review and customize the CREATE TABLE command that the wizard will run to create the destination table.  
  
> [!NOTE]  
>  If you're looking for info about the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] CREATE TABLE statement, and not about the **Create Table SQL Statement** dialog box of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard, see [CREATE TABLE &#40;Transact-SQL&#41;](../Topic/CREATE%20TABLE%20\(Transact-SQL\).md).  
  
 For more info about how the wizard maps data types from source columns to destination columns, see [How the Wizard maps data types from source to destination](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
> [!NOTE]  
>  If the **Create destination table** option and the **Edit SQL** button are disabled on the **Column Mappings** page, go back to the **Select Source Tables and Views** page and enter the name of a new table in the **Destination** column. After you specify a new destination table or tables and click **Next**, the **Create destination table** option is automatically selected and the **Edit SQL** button is enabled on the **Column Mappings** page. You can select **Edit SQL** to show the **Create Table SQL Statement** dialog box.  
  
## Screen shot  
 The following screen shot shows the **Create Table SQL Statement** dialog box of the Wizard. To take another look at the **Column Mappings** dialog box, see [Column Mappings &#40;SQL Server Import and Export Wizard&#41;](Column%20Mappings%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
 ![Create table page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Create-table.png "Create table")  
  
## Options on this page  
 **SQL statement**  
 Displays the auto\-generated SQL statement and lets you customize it. For more info about the CREATE TABLE statement and syntax, see [CREATE TABLE &#40;Transact-SQL&#41;](../Topic/CREATE%20TABLE%20\(Transact-SQL\).md).  
  
 If you change the default CREATE TABLE command, you may also have to make changes to the associated column mappings.  
  
 To include a carriage return in the text of the SQL statement, press CTRL\+ENTER. If you press ENTER alone, the dialog box closes.  
  
 **Autogenerate**  
 Restore the default SQL statement, if you have modified it, by clicking **Autogenerate**.  
  
## When the source table contains a FILESTREAM column  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard generates a default CREATE TABLE statement based on the connected data source. This default CREATE TABLE statement does not include the FILESTREAM attribute even if the source table has a FILESTREAM column. To copy a FILESTREAM column by using the wizard, first implement FILESTREAM storage on the destination database. Then, add the FILESTREAM attribute manually to the CREATE TABLE statement in the **Create Table** dialog box. For more info about FILESTREAM, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../Topic/Binary%20Large%20Object%20\(Blob\)%20Data%20\(SQL%20Server\).md).  
  
## What's next?  
 After you review and customize the CREATE TABLE command and click **OK**, the **Create Table SQL Statement** dialog box returns you to the **Column Mappings** dialog box. For more info, see [Column Mappings &#40;SQL Server Import and Export Wizard&#41;](../Topic/Column%20Mappings%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  