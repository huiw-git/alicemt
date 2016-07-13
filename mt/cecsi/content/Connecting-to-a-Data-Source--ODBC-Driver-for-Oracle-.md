---
title: Connecting to a Data Source (ODBC Driver for Oracle)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Connecting to a Data Source (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>An ODBC application can pass connection information in a number of ways. For example, the application might have the driver always prompt the user for connection information. Or the application might expect a connection string that specifies the data source connection. How you connect to a data source depends on the connection method used by your ODBC application.</para>
    <para>One common way to connect to a data source is through the Data Source dialog box. If your ODBC application is set up to use a dialog box, that dialog box is displayed and prompts you for the appropriate data source connection information.</para>
    <para>You can also connect to a data source using the <legacyLink xlink:href="0c360112-8720-4e54-a1a6-b9b18d943557">connection string</legacyLink>.</para>
    <procedure>
      <title>To connect to a data source using a dialog box</title>
      <steps class="ordered">
        <step>
          <content>
            <para>When the Data Source dialog box appears, select an Oracle data source and then click OK. The Connect dialog box appears.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Fill in the appropriate information for the Connect dialog box, and then click OK.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>After the connection information is verified, your application can use the ODBC Driver for Oracle to access the information that the data source contains.</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>