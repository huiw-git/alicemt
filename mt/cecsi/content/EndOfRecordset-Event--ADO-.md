---
title: "EndOfRecordset Event (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
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
# EndOfRecordset Event (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>EndOfRecordset</legacyBold> event is called when there is an attempt to move to a row past the end of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>EndOfRecordset</legacyBold> <parameterReference>fMoreData</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>fMoreData</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>VARIANT_BOOL</legacyBold> value that, if set to VARIANT_TRUE, indicates more rows have been added to the <legacyBold>Recordset</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value.</para>
          <para>When <legacyBold>EndOfRecordset</legacyBold> is called, this parameter is set to <legacyBold>adStatusOK </legacyBold>if the operation that caused the event was successful. It is set to <legacyBold>adStatusCantDeny</legacyBold> if this event cannot request cancellation of the operation that caused this event.   </para>
          <para>Before <legacyBold>EndOfRecordset</legacyBold> returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
        </definition>
        <definedTerm> <legacyItalic>pRecordset</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Recordset</legacyBold> object. The <legacyBold>Recordset</legacyBold> for which this event occurred.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>An <legacyBold>EndOfRecordset</legacyBold> event may occur if the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink> operation fails.</para>
      <para>This event handler is called when an attempt is made to move past the end of the <legacyBold>Recordset</legacyBold> object, perhaps as a result of calling <legacyBold>MoveNext</legacyBold>. However, while in this event, you could retrieve more records from a database and append them to the end of the <legacyBold>Recordset</legacyBold>. In that case, set <legacyItalic>fMoreData</legacyItalic> to VARIANT_TRUE, and return from <legacyBold>EndOfRecordset</legacyBold>. Then call <legacyBold>MoveNext</legacyBold> again to access the newly retrieved records.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>