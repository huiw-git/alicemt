---
title: Choose a Data Source (SQL Server Import and Export Wizard)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
---
# Choose a Data Source (SQL Server Import and Export Wizard)
  After the Welcome page, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Choose a Data Source**. On this page, you provide info about the source of your data and about how to connect to it.  
  
> [!TIP]  
>  If your data source requires a connection string, you can find examples on this third\-party site \- [The Connection Strings Reference](http://www.connectionstrings.com/).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Options  
 **Data Source**  
 Choose the data provider that matches the data storage format of the source.  
  
 There may be more than one provider available for your data source. For example, for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.  
  
 To load data from  an ODBC destination, select the .NET Framework Data Provider for ODBC.  
  
 The **Data Source** property has a variable number of options, which depend on the providers installed on the computer.  
  
## Dynamic options  
 The following sections list the important options for some frequently used data sources. Not all the data sources that are available in the **Data Source** drop\-down are listed here. For additional options and for other providers, see the provider\-specific documentation.  
  
## Data Source \= SQL Server Native Client or Microsoft OLE DB Provider for SQL Server  
 **Server name**  
 Type the name of the server that contains the data, or choose a server from the list.  
  
> [!NOTE]  
>  If you're on a network with multiple servers, it may be easier to type in the server name. If you click the drop\-down list, it may take a lot of time to query the network for all available servers, and your server name may not be listed in the results.  
  
 **Use Windows Authentication**  
 Specify whether the package should use [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Authentication to log in to the database. Windows Authentication is recommended for better security.  
  
 **Use SQL Server Authentication**  
 Specify whether the package should use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication to log in to the database. If you use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, you must provide a user name and password.  
  
 **User name**  
 Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 **Password**  
 Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 **Database**  
 Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 **Refresh**  
 Restore the list of available databases by clicking **Refresh**.  
  
## Data Source \= .NET Framework Data Provider for SQL Server  
 This page presents an alphabetical list of options for the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The most important options are listed in the following table.  
  
 **Data Source**  
 Type the name of the server that contains the data, or choose a server from the list.  
  
> [!NOTE]  
>  If you're on a network with multiple servers, it may be easier to type in the server name. If you click the drop\-down list, it may take a lot of time to query the network for all available servers, and your server name may not be listed in the results.  
  
 **Initial Catalog**  
 Type the name of the source database.  
  
 **Integrated Security**  
 Specify **True** to connect by using Windows integrated authentication, which is recommended, or **False** to connect by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. If you specify **False**, you must enter a user ID and password. The default value is **False**.  
  
 **User ID**  
 Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 **Password**  
 Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 The additional options that are listed when you select this provider are not required to connect successfully to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] source database. For a description of these additional options, see the documentation for the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] Software Development Kit.  
  
## Data Source \= Flat File Source  
 See the following Integration Services topics for information about the options for a flat file data source.  
  
 [Flat File Connection Manager Editor &#40;General Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(General%20Page\).md)  
  
 [Flat File Connection Manager Editor &#40;Columns Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)  
  
 [Flat File Connection Manager Editor &#40;Advanced Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)  
  
 [Flat File Connection Manager Editor &#40;Preview Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)  
  
## Data Source \= Microsoft Excel  
 **Excel file path**  
 Specify the path and file name for the spreadsheet from which to import the data. For example, **C:\\MyData.xlsx** or **\\\\Sales\\Database\\Northwind.xlsx**. Or, click **Browse**.  
  
 **Browse**  
 Locate the spreadsheet by using the **Open** dialog box.  
  
 **Excel version**  
 Select the version of Excel that is used by the source workbook.  
  
> [!NOTE]  
>  When [!INCLUDE[ofprexcel](../../Token\Other/ofprexcel_md.md)] is your data source, the wizard uses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] Excel Source component. For information about usage considerations and known issues, see [Excel Source](../../Topics\TopicNameNotContainA/Excel-Source.md).  
  
## Data Source \= Microsoft Access  
 **File name**  
 Specify the path and file name for the database file from which to import the data. For example, **C:\\MyData.mdb, \\\\Sales\\Database\\Northwind.mdb**. Or, click **Browse**.  
  
 **Browse**  
 Locate the database file by using the **Open** dialog box.  
  
 **User name**  
 Specify a valid user name for the database connection when a workgroup information file is associated with the database.  
  
 **Password**  
 Provide the user's password for the database connection when a workgroup information file is associated with the database. However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed by clicking **Advanced**.  
  
 **Advanced**  
 You may want to specify advanced options, such as the database password or a non\-default workgroup information file, by using the **Data Link Properties** dialog box.  
  
## Providers and drivers for Microsoft Excel and Access files  
 You may have to download the OLE DB providers and drivers for Microsoft Office files if they're not already installed. Later versions of the provider can open files created by earlier versions of Excel.  
  
 If the computer has a 32\-bit version of Office, then you have to install the 32\-bit version of the drivers, and you also have to ensure that you run the wizard or the Integration Services package that it creates in 32\-bit mode.  
  
|Microsoft Office version|Download|  
|------------------------------|--------------|  
|2007|[2007 Office System Driver: Data Connectivity Components](https://www.microsoft.com/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|  
  
## Data Source \= Azure Blob Source  
 To use the Azure Blob Source, you have to install the Azure Feature Pack for SSIS. For more info, see [Azure Feature Pack for Integration Services &#40;SSIS&#41;](../DocSets/Technical%20Documentation/NotInToc/Azure%20Feature%20Pack%20for%20Integration%20Services%20\(SSIS\).md).  
  
 **Storage account name**  
 Specify the name of the Azure storage account.  
  
 **Storage Key**  
 Provide the key for the Azure storage account.  
  
 **Use HTTPS**  
 Specify whether to use HTTP or HTTPS to connect to the storage account.  
  
 **Use local developer account**  
 Specify whether to use the storage emulator on the local computer.  
  
 **Blob container name**  
 Select from the list of storage containers available in the specified storage account.  
  
 **Blob file format**  
 Select Text or Avro file format.  
  
 **Column delimiter character**  
 If you selected Text format,  specify the column delimiter character.  
  
 **Use first row as column names**  
 Specify whether the first row of data contains column names.  
  
## What's next?  
 After you provide info about the source of your data and about how to connect to it, the next page is **Choose a Destination**. On this page, you provide info about the destination for your data and about how to connect to it. For more info, see [Choose a Destination &#40;SQL Server Import and Export Wizard&#41;](../Topic/Choose%20a%20Destination%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  