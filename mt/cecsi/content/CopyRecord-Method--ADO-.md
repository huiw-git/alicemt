---
title: "CopyRecord Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
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
# CopyRecord Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Copies an entity represented by a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">record</legacyLink> to another location.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Record</parameterReference><legacyBold>.CopyRecord (</legacyBold><parameterReference>Source</parameterReference><legacyBold>, </legacyBold><parameterReference>Destination</parameterReference><legacyBold>, </legacyBold><parameterReference>UserName</parameterReference><legacyBold>, </legacyBold><parameterReference>Password</parameterReference><legacyBold>, </legacyBold><parameterReference>Options</parameterReference><legacyBold>, </legacyBold><parameterReference>Async</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that contains a URL specifying the entity to be copied (for example, a file or directory). If <legacyItalic>Source </legacyItalic>is omitted or specifies an empty string, the file or directory represented by the current <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> will be copied.</para>
        </definition>
        <definedTerm> <legacyItalic>Destination</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that contains a URL specifying the location where <legacyItalic>Source</legacyItalic> will be copied.</para>
        </definition>
        <definedTerm> <legacyItalic>UserName</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that contains the user ID that, if needed, authorizes access to <legacyItalic>Destination</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Password</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that contains the password that, if needed, verifies <legacyItalic>UserName</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="2fa4eec5-d50b-4fd3-8ae7-40af441ba12b">CopyRecordOptionsEnum</legacyLink> value that has a default value of <legacyBold>adCopyUnspecified</legacyBold>. Specifies the behavior of this method.</para>
        </definition>
        <definedTerm> <legacyItalic>Async</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Boolean</languageKeyword> value that, when <languageKeyword>True</languageKeyword>, specifies that this operation should be asynchronous.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <returnValue>
    <content>
      <para>A <legacyBold>String </legacyBold>value that typically returns the value of <legacyItalic>Destination</legacyItalic>. However, the exact value returned is provider-dependent.</para>
    </content>
  </returnValue>
  <languageReferenceRemarks>
    <content>
      <para>The values of <legacyItalic>Source</legacyItalic> and <legacyItalic>Destination</legacyItalic> must not be identical; otherwise, a run-time error occurs. At least one of the server, path, or resource names must differ.</para>
      <para>All children (for example, subdirectories) of <legacyItalic>Source</legacyItalic> are copied recursively, unless <legacyBold>adCopyNonRecursive</legacyBold> is specified. In a recursive operation, <legacyItalic>Destination</legacyItalic> must not be a subdirectory of <legacyItalic>Source</legacyItalic>; otherwise, the operation will not complete.</para>
      <para>This method fails if <legacyItalic>Destination</legacyItalic> identifies an existing entity (for example, a file or directory), unless <legacyBold>adCopyOverWrite</legacyBold> is specified.</para>
      <alert class="important">
        <para>Use the <legacyBold>adCopyOverWrite</legacyBold> option judiciously. For example, specifying this option when copying a file to a directory will <legacyItalic>delete</legacyItalic> the directory and replace it with the file.</para>
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
        <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">record</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>