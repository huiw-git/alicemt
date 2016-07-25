---
title: "FetchProgress Event (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
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
# FetchProgress Event (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <unmanagedCodeEntityReference>FetchProgress</unmanagedCodeEntityReference><legacyBold> </legacyBold>event is called periodically during a lengthy asynchronous operation to report how many more rows have currently been retrieved into the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>FetchProgress</legacyBold> <parameterReference>Progress</parameterReference>, <parameterReference>MaxProgress</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>Progress </parameterReference>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value indicating the number of records that have currently been retrieved by the fetch operation.</para>
        </definition>
        <definedTerm>
          <parameterReference>MaxProgress </parameterReference>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value indicating the maximum number of records expected to be retrieved.</para>
        </definition>
        <definedTerm>
          <parameterReference>adStatus </parameterReference>
        </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value.</para>
        </definition>
        <definedTerm>
          <parameterReference>pRecordset </parameterReference>
        </definedTerm>
        <definition>
          <para>A <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object that is the object for which the records are being retrieved.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>When using <unmanagedCodeEntityReference>FetchProgress</unmanagedCodeEntityReference> with a child <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>, be aware that the <parameterReference>Progress</parameterReference> and <parameterReference>MaxProgress</parameterReference> parameter values are derived from the underlying <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Cursor Service</legacyLink> rowset. The values returned represent the total number of records in the underlying rowset, not just the number of records in the current chapter.</para>
      <alert class="note">
        <para>To use <unmanagedCodeEntityReference>FetchProgress</unmanagedCodeEntityReference> with Microsoft Visual Basic, Visual Basic 6.0 or later is required.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>