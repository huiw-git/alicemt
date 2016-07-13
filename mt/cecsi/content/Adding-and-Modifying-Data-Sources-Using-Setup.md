---
title: Adding and Modifying Data Sources Using Setup
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54b2d61d-6ce5-45af-a776-e03180470ecf
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Adding and Modifying Data Sources Using Setup
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>A data source identifies a path to data that can include a network library, server, database, and other attributes — in this case, the data source is the path to an Oracle database. To connect to a data source, the Driver Manager checks the Windows registry for specific connection information.</para>
    <para>The registry entry created by the ODBC Data Source Administrator is used by the ODBC Driver Manager and ODBC drivers. This entry contains information about each data source and its associated driver. Before you can connect to a data source, its connection information must be added to the registry.</para>
    <para>To add and configure data sources, use the <legacyLink xlink:href="a2f66b4c-a4ac-401b-8e95-d8f96332e0b5">ODBC Data Source Administrator</legacyLink>. The ODBC Administrator updates your data source connection information. As you add data sources, the ODBC Administrator updates the registry information for you.</para>
    <procedure>
      <title>To add a data source for Windows</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Open the ODBC Data Source Administrator.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the ODBC Data Source Administrator dialog box, click Add. The Creat New Data Source dialog box appears.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select Microsoft ODBC for Oracle and then click Finish. The Microsoft ODBC for Oracle Setup dialog box appears.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Data Source Name box, type the name of the data source you want to access. It can be any name that you choose.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Description box, type the description for the driver. This optional field describes the database driver that the data source connects to. It can be any name that you choose.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the User Name box, type your database user name (your database user ID).</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Server box, type the Database Alias or connect string for the Oracle Server engine that you want to access.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Click OK to add this data source. </para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <alert class="note">
            <para>The Data Sources dialog box appears, and the ODBC Administrator updates the registry information. The user name and connect string that you typed become the default connection values for this data source when you connect to it.</para>
          </alert>
          <list class="ordered">
            <listItem>
              <para>Click Options make more specifications about the ODBC Driver for Oracle setup: </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <legacyBold>Translation</legacyBold> — Click Select to choose a loaded data translator. The default is &lt;No Translator&gt;.</para>
                </listItem>
                <listItem>
                  <para>
                    <legacyBold>Performance</legacyBold> — The Include REMARKS in Catalog Functions check box specifies whether the driver returns Remarks columns for the <legacyLink xlink:href="98cced6f-41b8-43c1-a3cd-f4ea1615c0af">SQLColumns</legacyLink> result set. The ODBC Driver for Oracle provides faster access when this value is not set.  </para>
                  <para>The Include SYNONYMS in SQL Columns check box specifies whether the driver returns column information. <legacyBold>Buffer Size</legacyBold> specifies the size, in bytes, allocated to receive fetched data. The driver optimizes fetching so that one fetch from the Oracle Server returns enough rows to fill a buffer of the specified size. Larger values tend to increase performance when fetching a lot of data. </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyBold>Customization</legacyBold> — The Enforce ODBC DayOfWeek Standard check box specifies whether the result set will conform to the ODBC specified day-of-week format (Sunday = 1; Saturday = 7). If this check box is cleared, the locale-specific Oracle value is returned. </para>
                  <para>The SQLDescribeCol<legacyBold> always returns a value for precision</legacyBold> check box specifies whether or not the driver should return a non-zero value for the <legacyItalic>cbColDef</legacyItalic> argument of <legacyBold>SQLDescribeCol</legacyBold>. This connection string attribute applies only to columns where there is no Oracle-defined scale, such as computed numeric columns and columns defined as NUMBER without a precision or scale. A <legacyBold>SQLDescribeCol</legacyBold> call returns 130 for the precision when Oracle does not provide that information. If this check box is cleared, the driver will return 0 for these types of columns instead. </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>Click Add to add another data source, or click Close to exit.</para>
            </listItem>
          </list>
        </content>
      </conclusion>
    </procedure>
    <procedure>
      <title>To modify a data source for Windows</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Open the ODBC Data Source Administrator. Click the appropriate DSN tab.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select the Oracle data source you want to modify and then click Configure. The Microsoft ODBC for Oracle Setup dialog box appears.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Modify the applicable data source fields, and then click OK.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>When you have finished modifying the information in this dialog box, the ODBC Administrator updates the registry information.</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>