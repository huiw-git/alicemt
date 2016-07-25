---
title: "Driver-Specific Connection Information"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3748758a-f16a-4f3b-9c40-06f2e300704e
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver-Specific Connection Information
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>SQLConnect</legacyBold> assumes that a data source name, user ID, and password are sufficient to connect to a data source and that all other connection information can be stored on the system. This is frequently not the case. For example, a driver might need one user ID and password to log on to a server and a different user ID and password to log on to a DBMS. Because <legacyBold>SQLConnect</legacyBold> accepts a single user ID and password, this means that the other user ID and password must be stored with the data source information on the system if <legacyBold>SQLConnect</legacyBold> is to be used. This is a potential breach of security and should be avoided unless the password is encrypted.</para>
    <para>
      <legacyBold>SQLDriverConnect</legacyBold> allows the driver to define an arbitrary amount of connection information in the keyword-value pairs of the connection string. For example, suppose a driver requires a data source name, a user ID and password for the server, and a user ID and password for the DBMS. A custom program that always uses the XYZ Corp data source might prompt the user for IDs and passwords and build the following set of keyword-value pairs, or <legacyItalic>connection string,</legacyItalic> to pass to <legacyBold>SQLDriverConnect</legacyBold>:</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <codeInline>Trusted_Connection=yes</codeInline> instead of user ID and password information in the connection string.</para>
    </alert>
    <code>DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};</code>
    <para>The <legacyBold>DSN</legacyBold> (Data Source Name) keyword names the data source, the <legacyBold>UID</legacyBold> and <legacyBold>PWD</legacyBold> keywords specify the user ID and password for the server, and the <legacyBold>UIDDBMS</legacyBold> and <legacyBold>PWDDBMS</legacyBold> keywords specify the user ID and password for the DBMS. Notice that the final semicolon is optional. <legacyBold>SQLDriverConnect</legacyBold> parses this string; uses the XYZ Corp data source name to retrieve additional connection information from the system, such as the server address; and logs on to the server and DBMS using the specified user IDs and passwords.</para>
    <para>Keyword-value pairs in <legacyBold>SQLDriverConnect</legacyBold> must follow certain syntax rules. The keywords and their values should not contain the <legacyBold>[]{}(),;?*=!@</legacyBold> characters. The value of the <legacyBold>DSN</legacyBold> keyword cannot consist only of blanks and should not contain leading blanks. Because of the registry grammar, keywords and data source names cannot contain the backslash (\) character. Spaces are not allowed around the equal sign in the keyword-value pair.</para>
    <para>The <legacyBold>FILEDSN</legacyBold> keyword can be used in a call to <legacyBold>SQLDriverConnect</legacyBold> to specify the name of a file that contains data source information (see <legacyLink xlink:href="3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae">Connecting Using File Data Sources</legacyLink>, later in this section). The <legacyBold>SAVEFILE</legacyBold> keyword can be used to specify the name of a .dsn file in which the keyword-value pairs of a successful connection made by the call to <legacyBold>SQLDriverConnect</legacyBold> will be saved. For more information about file data sources, see the <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>