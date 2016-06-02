---
title: Choose a Destination (SQL Server Import and Export Wizard)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
---
# Choose a Destination (SQL Server Import and Export Wizard)
  After you provide info about the source of your data and about how to connect to it, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Choose a Destination**. On this page, you provide info about the destination for your data and about how to connect to it.  
  
 If you want to create a new SQL Server database as the destination, select SQL Server Native Client or the Microsoft OLE DB Provider for SQL Server. If you select the .NET Framework Data Provider for SQL Server, the option to create a new database is not available.  
  
> [!TIP]  
>  If your data source requires a connection string, you can find examples on this third\-party site \- [The Connection Strings Reference](http://www.connectionstrings.com/).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Static options on this page  
 **Destination**  
 Choose the data provider that matches the data storage format of the source.  
  
 There may be more than one provider available for your data source. For example, for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client, the Microsoft OLE DB Provider for SQL Server, or the .NET Framework Data Provider for SQL Server.  
  
 To save data to an ODBC destination, select the .NET Framework Data Provider for ODBC.  
  
 The **Destination** property has a variable number of options, which depend on the providers installed on the computer.  
  
## Dynamic options on this page  
 The following sections list the important options for some frequently used destinations. Not all the data sources that are available in the **Destination** drop\-down are listed here. For additional options and for other providers, see the provider\-specific documentation.  
  
## Destination \= SQL Server Native Client or Microsoft OLE DB Provider for SQL Server  
 **Server name**  
 Type the name of the server to receive the data, or choose a server from the list.  
  
> [!NOTE]  
>  If you're on a network with multiple servers, it may be easier to type in the server name. If you click the drop\-down list, it may take a lot of time to query the network for all available servers, and your server name may not be listed in the results.  
  
 **Use Windows Authentication**  
 Specify whether the package should use Microsoft Windows Authentication to log in to the database. Windows Authentication is recommended for better security.  
  
 **Use SQL Server Authentication**  
 Specify whether the package should use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication to log in to the database. If you use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, you must provide a user name and password.  
  
 **User name**  
 Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 **Password**  
 Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 **Database**  
 Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or create a new database by clicking **New**.  
  
 **Refresh**  
 Restore the list of available databases by clicking **Refresh**.  
  
 **New**  
 Create a new destination database by using the **Create Database** dialog box. For more info, see [Create Database &#40;SQL Server Import and Export Wizard&#41;](../Topic/Create%20Database%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
## Destination \= Flat File Destination  
 **File name**  
 Specify the path and file name for the file in which to store the data. Or, click **Browse** to locate a file.  
  
 **Browse**  
 Locate a file by using the **Open** dialog box.  
  
 **Locale**  
 Specify the locale ID \(LCID\) that defines character sort orders and date and time formatting.  
  
 **Unicode**  
 Indicate whether to use Unicode. If you use Unicode, you do not have to specify a code page.  
  
 **Code page**  
 Specify the code page for the language you want to use.  
  
 **Format**  
 Indicate whether to use delimited, fixed width, or ragged right formatting.  
  
|Value|Description|  
|-----------|-----------------|  
|Delimited|Columns are separated by a delimiter, specified on the **Columns** page.|  
|Fixed width|Columns have a fixed width.|  
|Ragged right|Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter.|  
  
 **Text qualifier**  
 Type the text qualifier to use. For example, you can specify that each text column be surrounded with quotation marks.  
  
 **Column names in first data row**  
 Indicate whether you want to display column names in the first data row.  
  
## Destination \= Microsoft Excel  
  
> [!NOTE]  
>  When you export data to a [!INCLUDE[ofprexcel](../../Token\Other/ofprexcel_md.md)] destination, the wizard uses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] Excel Destination component. For information about usage considerations and known issues, see [Excel Destination](../../Topics\TopicNameNotContainA/Excel-Destination.md).  
  
 **Excel file path**  
 Specify the path and file name for the workbook in which to store the data. For example, **C:\\MyData.xlsx** or **\\\\Sales\\Database\\Northwind.xlsx**. Or, click **Browse** to locate a workbook.  
  
 **Browse**  
 Locate an Excel workbook by using the **Open** dialog box.  
  
 **Excel version**  
 Select the version of Excel that is used by the destination workbook.  
  
## Destination \= Microsoft Access  
 **File name**  
 Specify the path and file name for the database file in which to store the data \(for example, C:\\MyData.mdb, \\\\Sales\\Database\\Northwind.mdb\). Or, click **Browse** to locate a database file.  
  
 **Browse**  
 Browse to the database file by using the **Open** dialog box.  
  
 **User name**  
 Specify a valid user name for the database connection when a workgroup information file is associated with the database.  
  
 **Password**  
 Provide the user's password for the database connection when a workgroup information file is associated with the database. However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed from the **Advanced** button.  
  
 **Advanced**  
 Specify advanced options, such as the database password or a non\-default workgroup information file, by using the **Data Link Properties** dialog box. For more information about OLE DB provider properties, search in the Data Access section of the [MSDN Library](http://go.microsoft.com/fwlink/?linkid=62553).  
  
## Providers and drivers for Microsoft Excel and Access files  
 You may have to download the OLE DB providers and drivers for Microsoft Office files if they're not already installed. Later versions of the provider can open files created by earlier versions of Excel.  
  
 If the computer has a 32\-bit version of Office, then you have to install the 32\-bit version of the drivers, and you also have to ensure that you run the wizard or the Integration Services package that it creates in 32\-bit mode.  
  
|Microsoft Office version|Download|  
|------------------------------|--------------|  
|2007|[2007 Office System Driver: Data Connectivity Components](https://www.microsoft.com/en-us/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/en-us/download/details.aspx?id=39358)|  
  
## Destination \= Azure Blob Destination  
 To use the Azure Blob Destination, you have to install the Azure Feature Pack for SSIS. Download the Feature Pack [here](http://go.microsoft.com/fwlink/?LinkId=626967).  
  
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
 After you provide info about the destination for your data and about how to connect to it, the next page is **Specify Table Copy or Query**. On this page, you specify whether you want to copy an entire table or only certain rows. For more info, see [Specify Table Copy or Query &#40;SQL Server Import and Export Wizard&#41;](../Topic/Specify%20Table%20Copy%20or%20Query%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  