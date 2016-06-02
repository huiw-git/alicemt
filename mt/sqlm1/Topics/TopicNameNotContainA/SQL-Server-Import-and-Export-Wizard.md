---
title: SQL Server Import and Export Wizard
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
---
# SQL Server Import and Export Wizard
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard is the simplest way to copy data from a source to a destination.  
  
 The wizard can also create a destination database and destination tables for you. However, if you have to copy a large number databases or tables, or other kinds of database objects, use the Copy Database Wizard instead. For more info, see [Use the Copy Database Wizard](../../Topics\TopicNameNotContainA/Use-the-Copy-Database-Wizard.md).  
  
## Get the SQL Server Import and Export Wizard  
 If you don't have [!INCLUDE[msCoName] (../Token/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installed on your computer, you can install the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard  by installing SQL Server Data Tools \(SSDT\). For more info, see [Download SQL Server Data Tools \(SSDT\)](https://msdn.microsoft.com/library/mt204009.aspx).  
  
 You may also have to install additional files to connect to certain data sources and destinations. For more info, see [Data sources that you can use](#wizardSources).  
  
## Start the Wizard  
 If you're ready to run the wizard, see [Start the SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/Start-the-SQL-Server-Import-and-Export-Wizard.md).  
  
##  <a name="wizardSources"></a> Data sources that you can use  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard can copy data to and from the following data sources.  
  
-   **Enterprise databases** \- [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], Oracle, and others.  
  
     [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] doesn't install the files that you need to connect to enterprise databases other than [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Oracle \- for example, to connect to IBM DB2 or Informix. If you already have the client software for your enterprise database system, then you typically have what you need to make a connection. If you don't have the client software installed, ask the database administrator how to install a licensed copy.  
  
-   **Open source databases** \- MySql, PostgreSQL, SQLite, and others.  
  
     You may have to download additional files to connect to these data sources.  
  
    -   For **MySql**, see [MySQL Connectors](http://dev.mysql.com/downloads/connector/).  
  
    -   For **PostgreSQL**, see [psqlODBC \- PostgreSQL ODBC driver](https://odbc.postgresql.org/) and third\-party products such as [Npgsql \- .NET Data Provider for PostgreSQL](http://www.npgsql.org/).  
  
    -   For **SQLite**, select from among several open source providers and drivers available online.  
  
-   **Microsoft Office files** \- Microsoft Excel and Microsoft Access.  
  
     Microsoft Office doesn't install all the files that you need to connect to Excel and Access files as data sources. Get the following download. [Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040).  
  
-   **Flat files**.  
  
-   **Cloud data sources** \- Azure Blob Storage.  
  
     [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] doesn't install the files that you need to connect to Azure Blob Storage as a data source. Get the following download. [Microsoft SQL Server 2016 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=49492).  
  
-   **Many other data sources**. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard can also copy data to and from the following sources.  
  
    -   Any source for which an **ODBC driver** is available, by using the .Net Framework Data Provider for ODBC.  
  
         You can make an ODBC \(Open Database Connectivity\) connection by selecting the .Net Framework Provider for Odbc on the **Choose a Data Source** or **Choose a Destination** page of the wizard, and then providing an existing DSN \(Data Source Name\) or a connection string.  
  
    -   Any source for which a **.Net Framework Data Provider** is available.  
  
    -   Any source for which an **OLE DB Provider** is available.  
  
    -   Other data sources for which **third\-party components** provide source and destination capabilities. Often these third\-party products are described as add\-on products for SQL Server Integration Services \(SSIS\).  
  
> [!TIP]  
>  If your data source requires a connection string, you can find examples on this third\-party site \- [The Connection Strings Reference](http://www.connectionstrings.com/).  
  
## Steps in the Wizard  
 The following table lists the steps for importing or exporting data and the corresponding pages of the Wizard. Depending on the options that you select in the Wizard, you don't typically see all of these pages.  
  
> [!TIP]  
>  Tap the F1 key from any page in the wizard to see documentation for the current page or dialog box.  
  
|Step|Wizard pages|  
|----------|------------------|  
|**Welcome**|[Welcome to SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/Welcome-to-SQL-Server-Import-and-Export-Wizard.md)|  
|**Pick the source** of the data.|[Choose a Data Source &#40;SQL Server Import and Export Wizard&#41;](../Topic/Choose%20a%20Data%20Source%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)|  
|**Pick the destination** for the data.|[Choose a Destination &#40;SQL Server Import and Export Wizard&#41;](../Topic/Choose%20a%20Destination%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)|  
|**Optional steps** to configure the destination.<br /><br /> -   Create a new destination database.<br />-   If you're copying data to a text file, configure additional settings.|[Create Database &#40;SQL Server Import and Export Wizard&#41;](../Topic/Create%20Database%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Configure Flat File Destination &#40;SQL Server Import and Export Wizard&#41;](../Topic/Configure%20Flat%20File%20Destination%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)|  
|**Specify what you want to copy.**|[Specify Table Copy or Query &#40;SQL Server Import and Export Wizard&#41;](../Topic/Specify%20Table%20Copy%20or%20Query%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Select Source Tables and Views &#40;SQL Server Import and Export Wizard&#41;](../Topic/Select%20Source%20Tables%20and%20Views%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Provide a Source Query &#40;SQL Server Import and Export Wizard&#41;](../Topic/Provide%20a%20Source%20Query%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)|  
|**Optional steps** to configure  the copy operation.<br /><br /> -   Create a new destination table.<br />-   Decide what to do if the Wizard doesn't have a set of data type mappings between the source and destination that you selected.<br />-   Review column mappings between source and destination.<br />-   Handle issues with converting data types between source and destination.<br />-   Preview the data to be copied.|[Create Table SQL Statement &#40;SQL Server Import and Export Wizard&#41;](../Topic/Create%20Table%20SQL%20Statement%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Convert Types without Conversion Checking &#40;SQL Server Import and Export Wizard&#41;](../Topic/Convert%20Types%20without%20Conversion%20Checking%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Column Mappings &#40;SQL Server Import and Export Wizard&#41;](../Topic/Column%20Mappings%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Review Data Type Mapping &#40;SQL Server Import and Export Wizard&#41;](../Topic/Review%20Data%20Type%20Mapping%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Column Conversion Details Dialog Box &#40;SQL Server Import and Export Wizard&#41;](../Topic/Column%20Conversion%20Details%20Dialog%20Box%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Preview Data Dialog Box &#40;SQL Server Import and Export Wizard&#41;](../Topic/Preview%20Data%20Dialog%20Box%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)|  
|**Copy the data.**<br /><br /> Optionally, save the SSIS package that the Wizard has created in memory.|[Save and Run Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20and%20Run%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Save SSIS Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Complete the Wizard &#40;SQL Server Import and Export Wizard&#41;](../Topic/Complete%20the%20Wizard%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)<br /><br /> [Performing Operation &#40;SQL Server Import and Export Wizard&#41;](../Topic/Performing%20Operation%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)|  
  
## Permissions you need to run the Wizard  
 To run the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard successfully, you have to have at least the following permissions:  
  
|Permission required|Permission required if you're using SQL Server|  
|-------------------------|----------------------------------------------------|  
|Permissions to connect to the source and destination databases or file shares.|Server and database login rights.|  
|Permission to read data from the source database or file.|SELECT permissions on the source tables and views.|  
|Permissions to write data to the destination database or file.|INSERT permissions on the destination tables.|  
||CREATE DATABASE or CREATE TABLE permissions.|  
|If you want to save the SSIS package created by the wizard, permissions sufficient to save the package to the **msdb** database or to the file system.|If you want to save the package to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], permissions sufficient to save the package to the **msdb** database.|  
  
##  <a name="wizardSSIS"></a> The Wizard uses SQL Server Integration Services \(SSIS\)  
 The Wizard uses SQL Server Integration Services \(SSIS\) to copy data. SSIS is an ETL tool for extracting, transforming, and loading data. The pages of the Wizard use some of the language of SSIS.   
  
 In SSIS, the basic unit is the **package**. The Wizard creates a package in memory as you move through the pages of the Wizard and specify options.  
  
For more info about SSIS, see [SQL Server Integration Services](../../Topics\TopicNameNotContainA/SQL-Server-Integration-Services.md).  
  
> [!NOTE]  
>  This section describes the option to save the SSIS package that the Wizard creates. You only have the option to save the package if you have [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Standard Edition or higher installed.  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard is the simplest way to create a basic [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package that copies data from a source to a destination. At the end of the Wizard, you can save the package. Later you can reuse the package and extend it by using [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer to add tasks, transformations, and event\-driven logic.  
  
 The method that you use to run the Wizard determines whether you can save and run the package that the Wizard creates.  
  
-   If you start the Wizard from the Start menu, from the command prompt, or from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], you can run the package immediately at the end of the Wizard by selecting the **Execute immediately** check box. By default, this check box is selected and the package runs immediately. Optionally, you can also save the package.  
  
-   If you start the Wizard from an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], you can't run the package until after you exit the wizard. The Wizard saves the package in the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project from which you started the wizard. You can run the package in [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)].  
  
##  <a name="wizardMapping"></a> How the Wizard maps data types from source to destination  
 In the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard, you can set the name, the data type, and the data type properties of columns in new destination tables and files, but you can't add other transformations for  column values. As a result, the fixed mapping of data types from source to destination is important.  
  
 The Wizard uses the mapping files that are installed by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] to map data types from one database version or system to another. For example, it can map from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data types to Oracle data types. By default, the mapping files in XML format are installed in the folder **C:\\Program Files\\Microsoft SQL Server\\130\\DTS\\MappingFiles**.  
  
-   **You can change the existing mapping files**. If your business requires different mappings between data types, you can update the mapping files to change the mappings used by the wizard. For example, if you want the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **nchar** data type to map to the DB2 **GRAPHIC** data type instead of the DB2 **VARGRAPHIC** data type when you transfer data from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to DB2, you can change the **nchar** mapping in the **SqlClientToIBMDB2.xml** mapping file to use **GRAPHIC** instead of **VARGRAPHIC.**  
  
-   **You can add a new mapping file**. [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] installs mappings between many commonly used combinations of source and destination. You can also add new mapping files to the **MappingFiles** directory to support additional sources and destinations. The new mapping files must conform to the published XSD schema and map between a unique combination of source and destination.  
  
 If you edit an existing mapping file, or add a new mapping file to the folder, you have to close and reopen the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to load the new or changed mapping file.  
  
 **Sample mapping file**  
  
 Here's a portion of the XML mapping file that maps from SQL Server to Oracle data types \(or, more specifically, from the data types used by the .Net Framework Data Provider for SQL Server to the data types used by the .NET Framework Data Provider for Oracle\).  
  
```xml  
  
<dtm:DataTypeMappings  
	xmlns:dtm="http://www.microsoft.com/SqlServer/Dts/DataTypeMapping.xsd"   
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
	SourceType="System.Data.SqlClient.SqlConnection"   
	MinSourceVersion="*"   
	MaxSourceVersion="*"   
	DestinationType="MSDAORA;OraOLEDB.Oracle;System.Data.OracleClient.OracleConnection"   
	MinDestinationVersion="08.*"   
	MaxDestinationVersion="*">  
  
	<!-- smallint -->  
	<dtm:DataTypeMapping >  
		<dtm:SourceDataType>  
			<dtm:DataTypeName>smallint</dtm:DataTypeName>  
		</dtm:SourceDataType>  
		<dtm:DestinationDataType>  
			<dtm:SimpleType>  
				<dtm:DataTypeName>INTEGER</dtm:DataTypeName>  
			</dtm:SimpleType>  
		</dtm:DestinationDataType>  
	</dtm:DataTypeMapping>	  
  
	<!-- int -->  
	<dtm:DataTypeMapping >  
		<dtm:SourceDataType>  
			<dtm:DataTypeName>int</dtm:DataTypeName>  
		</dtm:SourceDataType>  
		<dtm:DestinationDataType>  
			<dtm:SimpleType>  
				<dtm:DataTypeName>INTEGER</dtm:DataTypeName>  
			</dtm:SimpleType>  
		</dtm:DestinationDataType>  
	</dtm:DataTypeMapping>	  
  
        ...  
  
</dtm:DataTypeMappings>  
  
```  
  
## What's next?  
 Start the Wizard. For more info, see [Start the SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/Start-the-SQL-Server-Import-and-Export-Wizard.md).  
  
  