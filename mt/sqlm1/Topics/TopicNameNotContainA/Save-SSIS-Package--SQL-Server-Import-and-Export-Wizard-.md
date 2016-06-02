---
title: Save SSIS Package (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
---
# Save SSIS Package (SQL Server Import and Export Wizard)
  If you specified that you wanted to save the SSIS package created by the wizard,  the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Save SSIS Package**. On this page, you specify additional options for saving the package.  
  
 The options that you see on the **Save SSIS Package** page depend on the choice that you made on the **Save and Run Package** page to save the package to SQL Server or to the file system. To take another look at the **Save and Run Package** page, see [Save and Run Package &#40;SQL Server Import and Export Wizard&#41;](Save%20and%20Run%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Screen shots  
 The following screen shot shows the **Save SSIS Package** page of the Wizard after selecting the **SQL Server** option on the **Save and Run Package** page.  
  
 ![Save SSIS Package page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Save-package2.png "Save package2")  
  
 The following screen shot shows the **Save SSIS Package** page of the Wizard after selecting the **File system** option on the **Save and Run Package** page.  
  
 ![Save SSIS Package page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Save-package1.png "Save package1")  
  
## Options for saving the package  
 The **Save SSIS Package** page is one of two pages on which you pick options for saving the SSIS package.  
  
-   On the previous page, **Save and Execute Package**, you pick whether to save the package in SQL Server or as a file. You also pick security settings for the saved package. To take another look at the **Save and Run Package** page, see [Save and Run Package &#40;SQL Server Import and Export Wizard&#41;](Save%20and%20Run%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
-   On the current page, you provide a name for the package and more info about where to save it. For more info, see [Save SSIS Package \(SQL Server Import and Export Wizard\)](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
## Static options  
 **Name**  
 Provide a unique name for the package.  
  
 **Description**  
 Provide a description for the package. As a best practice, describe the package in terms of its purpose, to make packages self\-documenting and easier to maintain.  
  
 **Target**  
 View the target \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or file\) that was previously specified for the destination file.  
  
## Save the package in SQL Server  
 **Server name**  
 When you have selected a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] destination, type or select the destination server name.  
  
 The wizard saves the package  in the **sysssispackages** table of the **msdb** database.  
  
 **Use Windows Authentication**  
 When you have selected a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] destination, specify whether to connect to the server by using Windows Integrated Authentication. This is the preferred authentication method.  
  
 **Use SQL Server Authentication**  
 When you have selected a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] destination, specify whether to connect to the server by using SQL Server Authentication.  
  
 **User name**  
 When you have selected a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] user name.  
  
 **Password**  
 When you have selected a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] password.  
  
## Save the package in the File System  
 **File name**  
 Type the path and filename for the destination file, or use the **Browse** button to select a destination.  
  
> [!TIP]  
>  Be sure to specify a destination folder, either by typing or by browsing. If you only type the filename without a path, you don't know where the wizard saves the package. Or, the wizard may try to save the package to a location where you don't have permission to save a file, and raise an error.  
>   
>  Also, remember where you save the package file.  
  
 **Browse**  
 Optionally, browse to select the path for the destination file by using the **Save Package** dialog box.  
  
## Run the saved package again later  
 To learn how to run the saved package again later, see one the following topics.  
  
-   To run a package by using a utility program with a friendly user interface, see [Execute Package Utility &#40;DtExecUI&#41; UI Reference](../Topic/Execute%20Package%20Utility%20\(DtExecUI\)%20UI%20Reference.md).  
  
-   To run a package from the command line or from a batch file, see [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md).  
  
-   If you saved the package to the file system, see [Run a Package in SQL Server Data Tools](../../Topics\TopicNameContainA/Run-a-Package-in-SQL-Server-Data-Tools.md) to run the package in the development environment. You have to add the package to an Integration Services project before you can open and run it.  
  
-   If you saved the package to SQL Server, see [Run a Package on the SSIS Server Using SQL Server Management Studio](../../Topics\TopicNameContainA/Run-a-Package-on-the-SSIS-Server-Using-SQL-Server-Management-Studio.md).  
  
## Customize the saved package  
 To learn how to customize the saved package, see [Integration Services &#40;SSIS&#41; Packages](../Topic/Integration%20Services%20\(SSIS\)%20Packages.md).  
  
## What's next?  
 After you specify additional options for saving the package, the next page is **Complete the Wizard**. On this page, you review the choices that you made in the wizard. For more info, see [Complete the Wizard &#40;SQL Server Import and Export Wizard&#41;](../Topic/Complete%20the%20Wizard%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
## See Also  
 [Save Packages](../../Topics\TopicNameNotContainA/Save-Packages.md)  
  
  