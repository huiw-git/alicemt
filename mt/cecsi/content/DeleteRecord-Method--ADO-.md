---
title: "DeleteRecord Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
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
# DeleteRecord Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Deletes an entity represented by a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Record</parameterReference><legacyBold>.DeleteRecord </legacyBold><parameterReference>Source</parameterReference><legacyBold>, </legacyBold><parameterReference>Async</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that contains a URL identifying the entity (for example, the file or directory) to be deleted. If <legacyItalic>Source</legacyItalic> is omitted or specifies an empty string, the entity represented by the current <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> is deleted. If the Record is a collection record (<legacyLink xlink:href="790e46a2-13d2-451e-a8be-130bd9a206a4">RecordType</legacyLink> of <legacyBold>adCollectionRecord</legacyBold>, such as a directory) all children (for example, subdirectories) will also be deleted.</para>
        </definition>
        <definedTerm> <legacyItalic>Async</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Boolean</languageKeyword> value that, when <languageKeyword>True</languageKeyword>, specifies that the delete operation is asychronous.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Operations on the object represented by this <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> may fail after this method completes. After calling <unmanagedCodeEntityReference>DeleteRecord</unmanagedCodeEntityReference>, the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> should be closed because the behavior of the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> may become unpredictable depending upon when the provider updates the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> with the data source.</para>
      <para>If this <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> was obtained from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, then the results of this operation will not be reflected immediately in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>. Refresh the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> by closing and re-opening it, or by executing the <legacyBold>Recordset</legacyBold> <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method, the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method, or the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method.</para>
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
<link xlink:href="25bedc25-c51c-4cab-96ce-930b959965d9">Delete Method (ADO Fields Collection)</link>
<link xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete Method (ADO Parameters Collection)</link>
<link xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete Method (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>