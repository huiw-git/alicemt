---
title: SQL Server Browsing Example
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e0d5fd1-ec93-4348-a77a-08f5ba738bc6
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL Server Browsing Example
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following example shows how <legacyBold>SQLBrowseConnect</legacyBold> might be used to browse the connections available with a driver for SQL Server. First, the application requests a connection handle:</para>
    <code>SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc);</code>
    <para>Next, the application calls <legacyBold>SQLBrowseConnect</legacyBold> and specifies the SQL Server driver, using the driver description returned by <legacyBold>SQLDrivers</legacyBold>:</para>
    <code>SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,
                  sizeof(BrowseResult), &amp;BrowseResultLen);</code>
    <para>Because this is the first call to <legacyBold>SQLBrowseConnect</legacyBold>, the Driver Manager loads the SQL Server driver and calls the driver's <legacyBold>SQLBrowseConnect</legacyBold> function with the same arguments it received from the application.</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <codeInline>Trusted_Connection=yes</codeInline> instead of user ID and password information in the connection string.</para>
    </alert>
    <para>The driver determines that this is the first call to <legacyBold>SQLBrowseConnect</legacyBold> and returns the second level of connection attributes: server, user name, password, application name, and workstation ID. For the server attribute, it returns a list of valid server names. The return code from <legacyBold>SQLBrowseConnect</legacyBold> is SQL_NEED_DATA. Here is the browse result string:</para>
    <code>"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;
   *APP:AppName=?;*WSID:WorkStation ID=?;"</code>
    <para>Each keyword in the browse result string is followed by a colon and one or more words before the equal sign. These words are the user-friendly name that an application can use to build a dialog box. The <legacyBold>APP</legacyBold> and <legacyBold>WSID</legacyBold> keywords are prefixed by an asterisk, which means they are optional. The <legacyBold>SERVER</legacyBold>, <legacyBold>UID</legacyBold>, and <legacyBold>PWD</legacyBold> keywords are not prefixed by an asterisk; values must be supplied for them in the next browse request string. The value for the <legacyBold>SERVER</legacyBold> keyword may be one of the servers returned by <legacyBold>SQLBrowseConnect</legacyBold> or a user-supplied name.</para>
    <para>The application calls <legacyBold>SQLBrowseConnect</legacyBold> again, specifying the green server and omitting the <legacyBold>APP</legacyBold> and <legacyBold>WSID</legacyBold> keywords and the user-friendly names after each keyword:</para>
    <code>SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,
                  BrowseResult, sizeof(BrowseResult), &amp;BrowseResultLen);</code>
    <para>The driver attempts to connect to the green server. If there are any nonfatal errors, such as a missing keyword-value pair, <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_NEED_DATA and remains in the same state as it was prior to the error. The application can call <legacyBold>SQLGetDiagField</legacyBold> or <legacyBold>SQLGetDiagRec</legacyBold> to determine the error. If the connection is successful, the driver returns SQL_NEED_DATA and returns the browse result string:</para>
    <code>"*DATABASE:Database={master,model,pubs,tempdb};
   *LANGUAGE:Language={us_english,Franais};"</code>
    <para>Because the attributes in this string are optional, the application can omit them. However, the application must call <legacyBold>SQLBrowseConnect</legacyBold> again. If the application chooses to omit the database name and language, it specifies an empty browse request string. In this example, the application chooses the pubs database and calls <legacyBold>SQLBrowseConnect</legacyBold> a final time, omitting the <legacyBold>LANGUAGE</legacyBold> keyword and the asterisk before the <legacyBold>DATABASE</legacyBold> keyword:</para>
    <code>SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,
                  sizeof(BrowseResult), &amp;BrowseResultLen);</code>
    <para>Because the <legacyBold>DATABASE</legacyBold> attribute is the final connection attribute required by the driver, the browsing process is complete, the application is connected to the data source, and <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_SUCCESS. <legacyBold>SQLBrowseConnect</legacyBold> also returns the complete connection string as the browse result string:</para>
    <code>"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"</code>
    <para>The final connection string returned by the driver does not contain the user-friendly names after each keyword, nor does it contain optional keywords not specified by the application. The application can use this string with <legacyBold>SQLDriverConnect</legacyBold> to reconnect to the data source on the current connection handle (after disconnecting) or to connect to the data source on a different connection handle. For example:</para>
    <code>SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,
                  sizeof(ConnStrOut), &amp;ConnStrOutLen, SQL_DRIVER_NOPROMPT);</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>