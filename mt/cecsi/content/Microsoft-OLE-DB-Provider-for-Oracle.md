---
title: "Microsoft OLE DB Provider for Oracle"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
caps.latest.revision: 15
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Microsoft OLE DB Provider for Oracle
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use Oracle’s OLE DB provider.</para>
    </alert>
    <para>The Microsoft OLE DB Provider for Oracle allows ADO to access Oracle databases.</para>
  </introduction>
  <section>
    <title>Connection String Parameters</title>
    <content>
      <para>To connect to this provider, set the <legacyItalic>Provider</legacyItalic> argument of the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to:</para>
      <code>MSDAORA</code>
      <para>Reading the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property will return this string as well.</para>
      <para>If a join query with a keyset or dynamic cursor is executed in an Oracle database, an error occurs. Oracle only supports a static read-only cursor.</para>
    </content>
  </section>
  <section>
    <title>Typical Connection String</title>
    <content>
      <para>A typical connection string for this provider is:</para>
      <code>"Provider=MSDAORA;Data Source=<legacyItalic>serverName</legacyItalic>;User ID=<legacyItalic>MyUserID</legacyItalic>; Password=<legacyItalic>MyPassword</legacyItalic>;"</code>
      <para>The string consists of these keywords:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Keyword</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>Provider</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the OLE DB Provider for Oracle.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Data Source</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the name of a server.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>User ID</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Password</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user password.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Provider-Specific Connection Parameters</title>
    <content>
      <para>The provider supports several provider-specific connection parameters in addition to those defined by ADO. As with the ADO connection properties, these provider-specific properties can be set via the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection of a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> or as part of the <legacyBold>ConnectionString</legacyBold>.</para>
      <para>These parameters are fully described in the <legacyLink xlink:href="3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8">OLE DB Programmer's Reference</legacyLink>. The <legacyLink xlink:href="80d389dd-46ef-459f-b0d4-6f712fc4f32d">ADO Dynamic Property Index</legacyLink> provides a cross-reference between these parameter names and the corresponding OLE DB properties.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Parameter</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>Window Handle</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the window handle to use to prompt for additional information.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Locale Identifier</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates a unique 32-bit number (for example, 1033) that specifies preferences related to the user's language. These preferences indicate how dates and times are formatted, items are sorted alphabetically, strings are compared, and so on.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>OLE DB Services</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates a bitmask that specifies OLE DB services to enable or disable.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Prompt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates whether to prompt the user while a connection is being established.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Extended Properties</legacyBold>
              </para>
            </TD>
            <TD>
              <para>A string containing provider-specific, extended connection information. Use this property only for provider-specific connection information that cannot be described through the property mechanism.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
<link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>