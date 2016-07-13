---
title: Connection String Format and Attributes
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c360112-8720-4e54-a1a6-b9b18d943557
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Connection String Format and Attributes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>Instead of using a dialog box, some applications might require a connection string that specifies data source connection information. The connection string is made up of a number of attributes that specify how a driver connects to a data source. An attribute identifies a specific piece of information that the driver needs to know before it can make the appropriate data source connection. Each driver might have a different set of attributes, but the connection string format is always the same. A connection string has the following format:</para>
    <code>"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;&lt;Attribute&gt;=&lt;value&gt;]"</code>
    <alert class="note">
      <para>The Microsoft ODBC Driver for Oracle supports the connection string format of the first version of the driver, which used <codeInline>CONNECTSTRING</codeInline>= instead of <codeInline>SERVER=</codeInline>.</para>
    </alert>
    <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <codeInline>Trusted_Connection=yes</codeInline> instead of user ID and password information in the connection string.</para>
    <para>You must specify the data source name if you do not specify the UID, PWD, SERVER (or CONNECTSTRING), and DRIVER attributes. However, all other attributes are optional. If you do not specify an attribute, that attribute defaults to the one specified in the relevant DSN tab of the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box. The attribute value might be case-sensitive.</para>
    <para>The attributes for the connection string are as follows:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Attribute</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
          <TD>
            <para>Default value</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>DSN</para>
          </TD>
          <TD>
            <para>The data source name listed in the Drivers tab of the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box.</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PWD</para>
          </TD>
          <TD>
            <para>The password for the Oracle Server that you want to access. This driver supports limitations that Oracle places on passwords.</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SERVER</para>
          </TD>
          <TD>
            <para>The connect string for the Oracle Server that you want to access.</para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>UID</para>
          </TD>
          <TD>
            <para>The Oracle Server user name. Depending on your system, this attribute might not be optional — that is, certain databases and tables might require this attribute for security purposes.</para>
            <para>Use "/" to use Oracle's operating system authentication. </para>
          </TD>
          <TD>
            <para>""</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>BUFFERSIZE</para>
          </TD>
          <TD>
            <para>The optimal buffer size used when fetching columns.</para>
            <para>The driver optimizes fetching so that one fetch from the Oracle Server returns enough rows to fill a buffer of this size. Larger values tend to increase performance if you fetch a lot of data.</para>
          </TD>
          <TD>
            <para>65535</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SYNONYMCOLUMNS</para>
          </TD>
          <TD>
            <para>When this value is true (1), an SQLColumn( ) API call returns column information. Otherwise, SQLColumn( ) returns only columns for tables and views. The ODBC Driver for Oracle provides faster access when this value is not set.</para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>REMARKS</para>
          </TD>
          <TD>
            <para>When this value is true (1), the driver returns Remarks columns for the <legacyLink xlink:href="98cced6f-41b8-43c1-a3cd-f4ea1615c0af">SQLColumns</legacyLink> result set. The ODBC Driver for Oracle provides faster access when this value is not set.</para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>StdDayOfWeek</para>
          </TD>
          <TD>
            <para>Enforces the ODBC standard for the DAYOFWEEK scalar. By default this is turned on, but users who need the localized version can change the behavior to use whatever Oracle returns.</para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>GuessTheColDef</para>
          </TD>
          <TD>
            <para>Specifies whether or not the driver should return a non-zero value for the <legacyItalic>cbColDef</legacyItalic> argument of <legacyBold>SQLDescribeCol</legacyBold>. Applies only to columns where there is no Oracle-defined scale, such as computed numeric columns and columns defined as NUMBER without a precision or scale. A <legacyBold>SQLDescribeCol</legacyBold> call returns 130 for the precision when Oracle does not provide that information.</para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For example, a connection string that connects to the MyDataSource data source using the MyOracleServerOracle Server and the Oracle User MyUserID would be:</para>
    <code>"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"</code>
    <para>A connection string that connects to the MyOtherDataSource data source using operating system authentication and the MyOtherOracleServerOracle Server would be:</para>
    <code>"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>