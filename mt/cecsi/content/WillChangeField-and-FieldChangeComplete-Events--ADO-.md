---
title: "WillChangeField and FieldChangeComplete Events (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
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
# WillChangeField and FieldChangeComplete Events (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>WillChangeField</legacyBold> event is called before a pending operation changes the value of one or more <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects in the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. The <legacyBold>FieldChangeComplete</legacyBold> event is called after the value of one or more <legacyBold>Field</legacyBold> objects has changed.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>WillChangeField</legacyBold> <parameterReference>cFields</parameterReference>, <parameterReference>Fields</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference>
<legacyBold>FieldChangeComplete </legacyBold><parameterReference>cFields</parameterReference>, <parameterReference>Fields</parameterReference>, <parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>cFields</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> that indicates the number of <legacyBold>Field</legacyBold> objects in <legacyItalic>Fields</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Fields</legacyItalic> </definedTerm>
        <definition>
          <para>For <legacyBold>WillChangeField</legacyBold>, the <legacyItalic>Fields</legacyItalic> parameter is an array of <legacyBold>Variants</legacyBold> that contains <legacyBold>Field</legacyBold> objects with the original values. For <legacyBold>FieldChangeComplete</legacyBold>, the <legacyItalic>Fields</legacyItalic> parameter is an array of <legacyBold>Variants</legacyBold> that contains <legacyBold>Field</legacyBold> objects with the changed values.</para>
        </definition>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of <legacyItalic>adStatus</legacyItalic> is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise it is not set.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value. </para>
          <para>When <legacyBold>WillChangeField</legacyBold> is called, this parameter is set to <legacyBold>adStatusOK </legacyBold>if the operation that caused the event was successful. It is set to <legacyBold>adStatusCantDeny</legacyBold> if this event cannot request cancellation of the pending operation.   </para>
          <para>When <legacyBold>FieldChangeComplete</legacyBold> is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successful, or to <legacyBold>adStatusErrorsOccurred</legacyBold> if the operation failed.   </para>
          <para>Before <legacyBold>WillChangeField</legacyBold> returns, set this parameter to <legacyBold>adStatusCancel</legacyBold> to request cancellation of the pending operation.   </para>
          <para>Before <legacyBold>FieldChangeComplete</legacyBold> returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
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
      <para>A <legacyBold>WillChangeField</legacyBold> or <legacyBold>FieldChangeComplete</legacyBold> event may occur when setting the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property and calling the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method with field and value array parameters.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>