---
title: "MoveRecord Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6d2807b0-b861-4583-bcaf-fb0b82e0f2d0
caps.latest.revision: 11
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
# MoveRecord Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Moves the entity represented by a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> to another location.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Record</parameterReference>.<legacyBold>MoveRecord (</legacyBold><parameterReference>Source</parameterReference><legacyBold>, </legacyBold><parameterReference>Destination</parameterReference><legacyBold>, </legacyBold><parameterReference>UserName</parameterReference><legacyBold>, </legacyBold><parameterReference>Password</parameterReference><legacyBold>, </legacyBold><parameterReference>Options</parameterReference><legacyBold>, </legacyBold><parameterReference>Async</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains a URL identifying the <legacyBold>Record</legacyBold> to be moved. If <legacyItalic>Source </legacyItalic>is omitted or specifies an empty string, the object represented by this <legacyBold>Record</legacyBold> is moved. For example, if the <legacyBold>Record</legacyBold> represents a file, the contents of the file are moved to the location specified by <legacyItalic>Destination</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Destination</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains a URL specifying the location where <legacyItalic>Source</legacyItalic> will be moved.</para>
        </definition>
        <definedTerm> <legacyItalic>UserName</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains the user ID that, if needed, authorizes access to <legacyItalic>Destination</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Password</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> that contains the password that, if needed, verifies <legacyItalic>UserName</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="f53c2ce4-1021-4a45-92b8-775e8bebad99">MoveRecordOptionsEnum</legacyLink> value whose default value is <legacyBold>adMoveUnspecified</legacyBold>. Specifies the behavior of this method.</para>
        </definition>
        <definedTerm> <legacyItalic>Async</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Boolean</legacyBold> value that, when <legacyBold>True</legacyBold>, specifies this operation should be asynchronous.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <returnValue>
    <content>
      <para>A <legacyBold>String</legacyBold> value. Typically, the value of <legacyItalic>Destination</legacyItalic> is returned. However, the exact value returned is provider-dependent.</para>
    </content>
  </returnValue>
  <languageReferenceRemarks>
    <content>
      <para>The values of <legacyItalic>Source</legacyItalic> and <legacyItalic>Destination</legacyItalic> must not be identical; otherwise, a run-time error occurs. At least the server, path, and resource names must differ.</para>
      <para>For files moved using the Internet Publishing Provider, this method updates all hypertext links in files being moved unless otherwise specified by <legacyItalic>Options</legacyItalic>. This method fails if <legacyItalic>Destination</legacyItalic> identifies an existing object (for example, a file or directory), unless <legacyBold>adMoveOverWrite</legacyBold> is specified.</para>
      <alert class="note">
        <para>Use the <legacyBold>adMoveOverWrite</legacyBold> option judiciously. For example, specifying this option when moving a file to a directory will delete the directory and replace it with the file.</para>
      </alert>
      <para>Certain attributes of the <legacyBold>Record</legacyBold> object, such as the <legacyLink xlink:href="65120ce6-3900-4cd4-b322-3b9816d74737">ParentURL</legacyLink> property, will not be updated after this operation completes. Refresh the <legacyBold>Record</legacyBold> object's properties by closing the <legacyBold>Record</legacyBold>, then re-opening it with the URL of the location where the file or directory was moved.</para>
      <para>If this <legacyBold>Record</legacyBold> was obtained from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, the new location of the moved file or directory will not be reflected immediately in the <legacyBold>Recordset</legacyBold>. Refresh the <legacyBold>Recordset</legacyBold> by closing and re-opening it.</para>
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
<link xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move Method</link>
<link xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods</link>
<link xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>