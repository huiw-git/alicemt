---
title: Choosing a Data Source or Driver
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10aaf570-01ab-4478-8339-bdde2a5e3dd1
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Choosing a Data Source or Driver
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The data source or driver used by an application is sometimes hard-coded in the application. For example, a custom application written by an MIS department to transfer data from one data source to another would contain the names of those data sources—the application simply would not work with any other data sources. Another example is a vertical application, such as one used for order entry. Such an application always uses the same data source, which has a predefined schema known by the application.</para>
    <para>Other applications select the data source or driver at run time. Usually, these are generic applications that do ad hoc queries, such as a spreadsheet that uses ODBC to import data. Such applications usually list the available data sources or drivers and let users choose the ones they want to work with. Whether a generic application lists data sources, drivers, or both frequently depends on whether the application uses DBMS-based or file-based drivers.</para>
    <para>DBMS-based drivers usually require a complex set of connection information, such as the network address, network protocol, database name, and so on. The purpose of a data source is to hide all of this information. Therefore, the data source paradigm lends itself to use with DBMS-based drivers. An application can display a list of data sources to the user in one of two ways. It can call <legacyBold>SQLDriverConnect</legacyBold> with the <legacyBold>DSN</legacyBold> (Data Source Name) keyword and no associated value; the Driver Manager will display a list of data source names. If the application wants control over the appearance of the list, it calls <legacyBold>SQLDataSources</legacyBold> to retrieve a list of available data sources and constructs its own dialog box. This function is implemented by the Driver Manager and can be called before any drivers are loaded. The application then calls a connection function and passes it the name of the chosen data source.</para>
    <para>If a data source is not specified, the default data source indicated by the system information is used. (For more information, see <legacyLink xlink:href="a2259db8-feb7-4f0a-afc8-88e235d86be7">Default Subkey</legacyLink>.) If <legacyBold>SQLConnect</legacyBold> is called by using a <legacyItalic>ServerName</legacyItalic> argument that cannot be found, is a null pointer, or is "DEFAULT", the Driver Manager connects to the default data source. The default data source is also used if the connection string that is used in a call to <legacyBold>SQLDriverConnect</legacyBold> or <legacyBold>SQLBrowseConnect</legacyBold> contains the <legacyBold>DSN</legacyBold> keyword set to "DEFAULT" or if the specified data source is not found. Additionally, the default data source is used if the connection string that is used in a call to <legacyBold>SQLDriverConnect</legacyBold> does not contain the <legacyBold>DSN</legacyBold> keyword.</para>
    <para>With file-based drivers, it is possible to use a file paradigm. For data stored on the local computer, users frequently know that their data is in a particular file, such as Employee.dbf. Instead of selecting an unknown data source, it is easier for such users to select the file they know. To implement this, the application first calls <legacyBold>SQLDrivers</legacyBold>. This function is implemented by the Driver Manager and can be called before any drivers are loaded. <legacyBold>SQLDrivers</legacyBold> returns a list of available drivers; it also returns values for the <legacyBold>FileUsage</legacyBold> and <legacyBold>FileExtns</legacyBold> keywords. The <legacyBold>FileUsage</legacyBold> keyword explains whether file-based drivers treat files as tables, as does Xbase, or as databases, as does Microsoft® Access. The <legacyBold>FileExtns</legacyBold> keyword lists the file name extensions the driver recognizes, such as .dbf for an Xbase driver. Using this information, the application constructs a dialog box through which the user chooses a file. Based on the extension of the chosen file, the application then connects to the driver by calling <legacyBold>SQLDriverConnect</legacyBold> with the <legacyBold>DRIVER</legacyBold> keyword.</para>
    <para>There is nothing to stop an application from using a data source with a file-based driver or calling <legacyBold>SQLDriverConnect</legacyBold> with the <legacyBold>DRIVER</legacyBold> keyword to connect to a DBMS-based driver. Here are several common uses of the <legacyBold>DRIVER</legacyBold> keyword for DBMS-based drivers:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Not creating data sources.</legacyBold> For example, a custom application might use a particular driver and database. If the driver name and all information that is required to connect to the database is hard-coded in the application, users do not have to create a data source on their computer to run the application. All they must do is install the application and driver. </para>
        <para>A disadvantage of this method is that the application must be recompiled and redistributed if the connection information changes. If a data source name is hard-coded in the application instead of complete connection information, each user must change only the information in the data source. </para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Accessing a particular DBMS a single time.</legacyBold> For example, a spreadsheet that retrieves data by calling ODBC functions might contain the <legacyBold>DRIVER</legacyBold> keyword to identify a particular driver. Because the driver name is meaningful to any users who have that driver, the spreadsheet could be passed among those users. If the spreadsheet contained a data source name, each user would have to create the same data source to use the spreadsheet.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Browsing the system for all databases accessible to a particular driver.</legacyBold> For more information, see <legacyLink xlink:href="6c2e9f76-b766-48df-b109-246bb05ae45d">Connecting with SQLBrowseConnect</legacyLink>, later in this section.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>