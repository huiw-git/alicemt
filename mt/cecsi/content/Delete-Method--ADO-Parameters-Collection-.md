---
title: "Delete Method (ADO Parameters Collection)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
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
# Delete Method (ADO Parameters Collection)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Deletes an object from the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Parameters.Delete</legacyBold> <parameterReference>Index</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Index</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains the name of the object you want to delete, or the object's ordinal position (index) in the collection.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Using the <unmanagedCodeEntityReference>Delete</unmanagedCodeEntityReference> method on a collection lets you remove one of the objects in the collection. This method is available only on the <unmanagedCodeEntityReference>Parameters</unmanagedCodeEntityReference> collection of a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object. You must use the <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object's <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property or its collection index when calling the <unmanagedCodeEntityReference>Delete</unmanagedCodeEntityReference> method—an object variable is not a valid argument.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25bedc25-c51c-4cab-96ce-930b959965d9">Delete Method (ADO Fields Collection)</link>
<link xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete Method (ADO Recordset)</link>
<link xlink:href="2726498c-dbd8-4266-983b-ae7d62c39142">DeleteRecord Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>