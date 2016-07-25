---
title: "Open Method (ADO Connection)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
caps.latest.revision: 12
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
# Open Method (ADO Connection)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Opens a connection to a data source.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>connection</parameterReference><legacyBold>.Open</legacyBold> <parameterReference>ConnectionString</parameterReference><legacyBold>, </legacyBold><parameterReference>UserID</parameterReference><legacyBold>, </legacyBold><parameterReference>Password, Options</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ConnectionString</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains connection information. See the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property for details on valid settings.</para>
        </definition>
        <definedTerm> <legacyItalic>UserID</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains a user name to use when establishing the connection.</para>
        </definition>
        <definedTerm> <legacyItalic>Password</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains a password to use when establishing the connection.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="bff07eeb-dee3-4e4e-9b2d-d56061ea744d">ConnectOptionEnum</legacyLink> value that determines whether this method should return after (synchronously) or before (asynchronously) the connection is established.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Using the <legacyBold>Open</legacyBold> method on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object establishes the physical connection to a data source. After this method successfully completes, the connection is live and you can issue commands against it and process the results.</para>
      <para>Use the optional <legacyItalic>ConnectionString</legacyItalic> argument to specify either a connection string containing a series of <legacyItalic>argument</legacyItalic> <legacyItalic>= value</legacyItalic> statements separated by semicolons, or a file or directory resource identified with a URL. The <legacyBold>ConnectionString</legacyBold> property automatically inherits the value used for the <legacyItalic>ConnectionString</legacyItalic> argument. Therefore, you can either set the <legacyBold>ConnectionString</legacyBold> property of the <legacyBold>Connection</legacyBold> object before opening it, or use the <legacyItalic>ConnectionString</legacyItalic> argument to set or override the current connection parameters during the <legacyBold>Open</legacyBold> method call.</para>
      <para>If you pass user and password information both in the <legacyItalic>ConnectionString</legacyItalic> argument and in the optional <legacyItalic>UserID</legacyItalic> and <legacyItalic>Password</legacyItalic> arguments, the <legacyItalic>UserID</legacyItalic> and <legacyItalic>Password</legacyItalic> arguments will override the values specified in <legacyItalic>ConnectionString</legacyItalic>.</para>
      <para>When you have concluded your operations over an open <legacyBold>Connection</legacyBold>, use the <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> method to free any associated system resources. Closing an object does not remove it from memory; you can change its property settings and use the <legacyBold>Open</legacyBold> method to open it again later. To completely eliminate an object from memory, set the object variable to <legacyItalic>Nothing</legacyItalic>.</para>
      <alert class="note">
        <para>
          <legacyBold> Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Connection</legacyBold> object, the <legacyBold>Open</legacyBold> method doesn't actually establish a connection to the server until a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> is opened on the <legacyBold>Connection</legacyBold> object.</para>
      </alert>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="1311d561-0e86-40f5-8cbc-ad8f13e626d1">Visual Basic Example</link>
<link xlink:href="66eca011-e258-4d8f-bd67-e017bcf0871b">VBScript Example</link>
<link xlink:href="f74a81fd-cbcc-4143-b9f8-774c88dd4fad">Visual C++ Example</link>
<link xlink:href="0b7dd9f8-4751-48fb-a75d-c6f75d80d928">Visual J++ Example</link>
<link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
<link xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>