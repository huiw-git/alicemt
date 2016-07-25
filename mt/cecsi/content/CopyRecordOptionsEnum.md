---
title: "CopyRecordOptionsEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
caps.latest.revision: 10
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
# CopyRecordOptionsEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the behavior of the <legacyLink xlink:href="b9bcf272-3c74-479f-95dd-0229a32e98fc">CopyRecord</legacyLink> method.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Constant</para>
          </TD>
          <TD>
            <para>Value</para>
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
              <legacyBold>adCopyAllowEmulation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Indicates that the <parameterReference>Source</parameterReference> provider attempts to simulate the copy using download and upload operations if this method fails due to <parameterReference>Destination</parameterReference><legacyItalic> </legacyItalic>being on a different server or is serviced by a different provider than <parameterReference>Source</parameterReference>. Note that differing provider capabilities may hamper performance or lose data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCopyNonRecursive</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Copies the current directory, but none of its subdirectories, to the destination. The copy operation is not recursive.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCopyOverWrite</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Overwrites the file or directory if the <parameterReference>Destination</parameterReference> points to an existing file or directory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCopyUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Default. Performs the default copy operation: The operation fails if the destination file or directory already exists, and the operation copies recursively.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>These constants do not have ADO/WFC equivalents.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="b9bcf272-3c74-479f-95dd-0229a32e98fc">CopyRecord Method (ADO)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>