---
title: Connecting Using File Data Sources
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Connecting Using File Data Sources
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The connection information for a file data source is stored in a .dsn file. As a result, the connection string can be used repeatedly by a single user or shared among several users if they have the appropriate driver installed. The file contains a driver name (or another data source name in the case of an unshareable file data source) and optionally, a connection string that can be used by <legacyBold>SQLDriverConnect</legacyBold>. The Driver Manager builds the connection string for the call to <legacyBold>SQLDriverConnect</legacyBold> from the keywords in the .dsn file.</para>
    <para>A file data source allows an application to specify connection options without having to build a connection string for use with <legacyBold>SQLDriverConnect</legacyBold>. The file data source usually is created by specifying the <legacyBold>SAVEFILE</legacyBold> keyword, which causes the Driver Manager to save the output connection string created by a call to <legacyBold>SQLDriverConnect</legacyBold> to the .dsn file. That connection string can be used repeatedly by calling <legacyBold>SQLDriverConnect</legacyBold> with the <legacyBold>FILEDSN</legacyBold> keyword. This streamlines the connection process and provides a persistent source of the connection string.</para>
    <para>File data sources also can be created by calling <legacyBold>SQLCreateDataSource</legacyBold> in the installer DLL. Information can be written into the .dsn file by calling <legacyBold>SQLWriteFileDSN</legacyBold>, and read from the .dsn file by calling <legacyBold>SQLReadFileDSN</legacyBold>; both of these functions are also in the installer DLL. For information about the installer DLL, see <legacyLink xlink:href="f11985c2-c054-4ab4-840e-aca4c585c9d8">Configuring Data Sources</legacyLink>.</para>
    <para>The keywords used for connection information are in the [ODBC] section of a .dsn file. The minimum information that a shareable .dsn file would have in the [ODBC] section is the DRIVER keyword:</para>
    <code>DRIVER = SQL Server</code>
    <para>The shareable .dsn file usually contains a connection string, as follows:</para>
    <code>DRIVER = SQL Server
UID = Larry
DATABASE = MyDB</code>
    <para>When the file data source is unshareable, the .dsn file contains only a <legacyBold>DSN</legacyBold> keyword. When the Driver Manager is sent the information in an unshareable file data source, it connects as necessary to the data source indicated by the <legacyBold>DSN</legacyBold> keyword. An unshareable .dsn file would contain the following keyword:</para>
    <code>DSN = MyDataSource</code>
    <para>The connection string used for a file data source is the union of the keywords specified in the .dsn file and the keywords specified in the connection string in the call to <legacyBold>SQLDriverConnect</legacyBold>. If any of the keywords in the .dsn file conflict with keywords in the connection string, the Driver Manager decides which keyword value should be used. For more information, see <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>.</para>
  </introduction>
  <relatedTopics>
<externalLink><linkText>http://support.microsoft.com/kb/165866</linkText><linkUri>http://support.microsoft.com/kb/165866</linkUri></externalLink>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>