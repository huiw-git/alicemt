---
title: "Open Method (ADO Record)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
caps.latest.revision: 14
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
# Open Method (ADO Record)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Opens an existing <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object, or creates a new item represented by the <legacyBold>Record</legacyBold>, such as a file or directory.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Open </legacyBold><parameterReference>Source</parameterReference><legacyBold>, </legacyBold><parameterReference>ActiveConnection</parameterReference><legacyBold>, </legacyBold><parameterReference>Mode</parameterReference><legacyBold>, </legacyBold><parameterReference>CreateOptions</parameterReference><legacyBold>, </legacyBold><parameterReference>Options</parameterReference><legacyBold>, </legacyBold><parameterReference>UserName</parameterReference><legacyBold>, </legacyBold><parameterReference>Password</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> that may represent the URL of the entity to be represented by this <legacyBold>Record</legacyBold> object, a <legacyBold>Command</legacyBold>, an open <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> or another <legacyBold>Record</legacyBold> object, a string that contains an SQL SELECT statement or a table name.</para>
        </definition>
        <definedTerm> <legacyItalic>ActiveConnection</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Variant</legacyBold> that represents the connect string or open <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Mode</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="3792c294-5161-4538-a908-22a5fc50b85f">ConnectModeEnum</legacyLink> value that specifies the access mode for the resultant <legacyBold>Record</legacyBold> object. Default value is <legacyBold>adModeUnknown</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>CreateOptions</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="6d746670-0850-4065-9cd4-168dea1d3ea9">RecordCreateOptionsEnum</legacyLink> value that specifies whether an existing file or directory should be opened, or a new file or directory should be created. Default value is <legacyBold>adFailIfNotExists</legacyBold>. If set to the default value, the access mode is obtained from the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property. This parameter is ignored when the <legacyItalic>Source</legacyItalic> parameter does not contain a URL.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="9028aba4-90fc-4dfc-88e4-fa8a7b6fedee">RecordOpenOptionsEnum</legacyLink> value that specifies options for opening the <legacyBold>Record</legacyBold>. Default value is <legacyBold>adOpenRecordUnspecified</legacyBold>. These values can be combined.</para>
        </definition>
        <definedTerm> <legacyItalic>UserName</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains the user ID that, if it is required, authorizes access to <legacyItalic>Source</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Password</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains the password that, if it is required, verifies <legacyItalic>UserName</legacyItalic>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyItalic>Source</legacyItalic> may be:  </para>
      <list class="bullet">
        <listItem>
          <para>A URL. If the protocol for the URL is http, the Internet Provider will be invoked by default. If the URL points to a node that contains an executable script (such as an .ASP page), a <legacyBold>Record</legacyBold> that contains the source instead of the executed contents is opened by default. Use the <legacyItalic>Options</legacyItalic> argument to modify this behavior.</para>
        </listItem>
        <listItem>
          <para>A <legacyBold>Record</legacyBold> object. A <legacyBold>Record</legacyBold> object opened from another <legacyBold>Record</legacyBold> will clone the original <legacyBold>Record</legacyBold> object.</para>
        </listItem>
        <listItem>
          <para>A <legacyBold>Command</legacyBold> object. The opened <legacyBold>Record</legacyBold> object represents the single row returned by executing the <legacyBold>Command</legacyBold>. If the results contain more than a single row, the contents of the first row are placed in the record and an error may be added to the <legacyBold>Errors</legacyBold> collection.</para>
        </listItem>
        <listItem>
          <para>An SQL SELECT statement. The opened <legacyBold>Record</legacyBold> object represents the single row returned by executing the contents of the string. If the results contain more than a single row, the contents of the first row are placed in the record and an error may be added to the <legacyBold>Errors</legacyBold> collection.</para>
        </listItem>
        <listItem>
          <para>A table name.</para>
        </listItem>
      </list>
      <para>If the <legacyBold>Record</legacyBold> object represents an entity that cannot be accessed with a URL (for example, a row of a <legacyBold>Recordset</legacyBold> derived from a database), the values of both the <legacyLink xlink:href="65120ce6-3900-4cd4-b322-3b9816d74737">ParentURL</legacyLink> property and the field accessed with the <legacyBold>adRecordURL</legacyBold> constant are null.</para>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
<link xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>