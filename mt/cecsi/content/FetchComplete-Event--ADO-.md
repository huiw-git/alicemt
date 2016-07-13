---
title: FetchComplete Event (ADO)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
manager:sonalm
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
# FetchComplete Event (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>FetchComplete</legacyBold> event is called after all the records in a lengthy asynchronous operation have been retrieved into the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>FetchComplete</legacyBold> <parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of <legacyBold>adStatus</legacyBold> is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise it is not set.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value. When this event is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successfull, or to <legacyBold>adStatusErrorsOccurred</legacyBold> if the operation failed.</para>
          <para>Before this event returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
        </definition>
        <definedTerm> <legacyItalic>pRecordset</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Recordset</legacyBold> object. The object for which the records were retrieved.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>To use <legacyBold>FetchComplete</legacyBold> with Microsoft Visual Basic, Visual Basic 6.0 or later is required.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>