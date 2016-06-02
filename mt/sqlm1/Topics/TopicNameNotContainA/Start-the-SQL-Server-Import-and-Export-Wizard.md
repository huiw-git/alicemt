---
title: Start the SQL Server Import and Export Wizard
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
---
# Start the SQL Server Import and Export Wizard
  Run the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard to copy data between a variety of sources and destinations.  
  
 This page describes how to start the Wizard. If you're looking for info about the Wizard and how it works, including a list of the steps in the wizard, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
> [!TIP]  
>  Tap the F1 key from any page in the wizard to see documentation for the current page or dialog box.  
  
## Get the SQL Server Import and Export Wizard  
 If you don't have [!INCLUDE[msCoName] (../Token/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installed on your computer, you can install the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard  by installing SQL Server Data Tools \(SSDT\). For more info, see [Download SQL Server Data Tools \(SSDT\)](https://msdn.microsoft.com/library/mt204009.aspx).  
  
 You may also have to install additional files to connect to certain data sources and destinations. For more info, see [Data sources that you can use](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Start the wizard from SQL Server Management Studio \(SSMS\)  
 In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], expand **Databases**, right\-click a database, point to **Tasks**, and then click one of the following options.  
  
-   **Import Data**  
  
-   **Export Data**  
  
## Start the wizard from the Start menu  
 On the **Start** menu, click **All apps**, find and expand **Microsoft SQL Server 2016** , and then click one of the following options.  
  
-   **SQL Server 2016 Import and Export Data \(64\-bit\)**  
  
-   **SQL Server 2016 Import and Export Data \(32\-bit\)**  
  
 Run the 64\-bit version of the Wizard unless you know that your data source requires a 32\-bit data provider.  
  
## Start the wizard from the command prompt  
 In a Command Prompt window, run **DTSWizard.exe** from one of the following locations.  
  
-   **C:\\Program Files\\Microsoft SQL Server\\130\\DTS\\Binn** for the 64\-bit version.  
  
-   **C:\\Program Files \(x86\)\\Microsoft SQL Server\\130\\DTS\\Binn** for the 32\-bit version.  
  
 Run the 64\-bit version of the Wizard unless you know that your data source requires a 32\-bit data provider.  
  
## Start the wizard from Visual Studio with SQL Server Data Tools \(SSDT\)  
 In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], with an Integration Services project open, do one of the following things.  
  
-   On the **Project** menu, click **SSIS Import and Export Wizard**.  
  
-   In Solution Explorer, right\-click the **SSIS Packages** folder, and then click **SSIS Import and Export Wizard**.  
  
## What's next?  
 When you start the Wizard, the first page is **Welcome to SQL Server Import and Export Wizard**. You don't have to take any action on this page. For more info, see [Welcome to SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/Welcome-to-SQL-Server-Import-and-Export-Wizard.md).  
  
 After the Welcome page, the next page is **Choose a Data Source**. On this page, you provide info about the source of your data and about how to connect to it. For more info, see [Choose a Data Source &#40;SQL Server Import and Export Wizard&#41;](../Topic/Choose%20a%20Data%20Source%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  