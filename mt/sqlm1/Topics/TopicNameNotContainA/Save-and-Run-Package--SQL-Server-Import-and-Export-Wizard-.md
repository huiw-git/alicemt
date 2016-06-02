---
title: Save and Run Package (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
---
# Save and Run Package (SQL Server Import and Export Wizard)
  After you specify and configure your data source and destination, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Save and Run Package**. On this page, you specify whether you want to run the copy operation immediately. Depending on your configuration, you may also be able to save the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package created by the wizard  to customize it and to reuse it.  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## What's a package?  
 The Wizard uses SQL Server Integration Services \(SSIS\) to copy data. In SSIS, the basic unit is the package. For more info, see [The Wizard uses SQL Server Integration Services (SSIS)](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Screen shot  
 The following screen shot shows the **Save and Run Package** page of the Wizard.  
   
 If you choose to save the package, there are additional options on the next page, **Save SSIS Package**.  
  
 ![Save and run package page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Save-and-run.png "Save and run")  
  
## Options for running and saving the package  
 To continue, you have to select at least one of the following options.  
  
 **Run immediately**  
 Select this option to run the package immediately.  
  
 **Save SSIS Package**  
 Save the package to run later, with the option to run it immediately. This option is available only if you have [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Standard Edition or a higher edition installed.  
  
If you choose to save the package, there are additional options on the next page, **Save SSIS Package**.  
  
> [!NOTE]  
>  If you stop a package before it finishes running, the package is not saved, even if you selected the **Save** check box.  
  
## Options for saving the package  
 The **Save and Run Package** page is one of two pages on which you pick options for saving the SSIS package.  
  
-   On the current page, you pick whether to save the package in SQL Server or as a file. You also pick security settings for the saved package.  
  
-   Next, on the **Save SSIS Package** page, you provide a name for the package and more info about where to save it. For more info, see [Save SSIS Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
 These options are available only if you select the **Save SSIS Package** option.  
  
 **SQL Server**  
 Select this option to save the package  in the **sysssispackages** table of the **msdb** database.  
  
 You select the target server and provide credentials to connect  to the server on the next page, **Save SSIS Package**. For more info, see [Save SSIS Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
 **File system**  
 Select this option to save the package as a file that has the .dtsx extension.  
  
 You select the target folder and file name for the package on the next page, **Save SSIS Package**. For more info, see [Save SSIS Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
 **Package protection level**  
 Select a protection level from the list to helps protect only sensitive data or all the data in the package.  
  
 The protection level determines the protection method, the password or user key, and the scope of package protection. Protection can include all data or sensitive data only. For more info about the available options, see [Access Control for Sensitive Data in Packages](../../Topics\TopicNameNotContainA/Access-Control-for-Sensitive-Data-in-Packages.md).  
  
 **Password**  
 Type a password.  
  
> [!NOTE]  
>  This option is available only if you set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.  
  
 **Retype password**  
 Type the password again.  
  
> [!NOTE]  
>  This option is available only if you set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.  
  
## Run the saved package again later  
 To learn how to run the saved package again later, see one the following topics.  
  
-   To run a package by using a utility program with a friendly user interface, see [Execute Package Utility &#40;DtExecUI&#41; UI Reference](../Topic/Execute%20Package%20Utility%20\(DtExecUI\)%20UI%20Reference.md).  
  
-   To run a package from the command line or from a batch file, see [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md).  
  
-   If you saved the package to the file system, see [Run a Package in SQL Server Data Tools](../../Topics\TopicNameContainA/Run-a-Package-in-SQL-Server-Data-Tools.md) to run the package in the development environment. You have to add the package to an Integration Services project before you can open and run it.  
  
-   If you saved the package to SQL Server, see [Run a Package on the SSIS Server Using SQL Server Management Studio](../../Topics\TopicNameContainA/Run-a-Package-on-the-SSIS-Server-Using-SQL-Server-Management-Studio.md).  
  
## Customize the saved package  
 To learn how to customize the saved package, see [Integration Services &#40;SSIS&#41; Packages](../Topic/Integration%20Services%20\(SSIS\)%20Packages.md).  
  
## What's next?  
 After you specify whether to run the copy operation and to save the package, the next page depends on the options that you choose.  
  
-   If you selected the option to run the package immediately, the next page is **Complete the Wizard**. On this page, you review the choices that you made in the wizard. For more info, see [Complete the Wizard &#40;SQL Server Import and Export Wizard&#41;](../Topic/Complete%20the%20Wizard%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
-   If you selected the option to save the package, the next page is **Save SSIS Package**. \(After you save the package, the next page is **Complete the Wizard**.\) On this page, you specify additional options for saving the package. For more info, see [Save SSIS Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
## See Also  
 [Execution of Projects and Packages](../../Topics\TopicNameNotContainA/Execution-of-Projects-and-Packages.md)   
 [Save Packages](../../Topics\TopicNameNotContainA/Save-Packages.md)  
  
  