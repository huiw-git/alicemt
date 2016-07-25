---
title: "ExecuteComplete Event (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
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
# ExecuteComplete Event (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>ExecuteComplete </legacyBold>event is called after a command has finished executing.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>ExecuteComplete</legacyBold> <parameterReference>RecordsAffected</parameterReference>, <parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pCommand</parameterReference>, <parameterReference>pRecordset</parameterReference>, <parameterReference>pConnection</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>RecordsAffected</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value indicating the number of records affected by the command.</para>
        </definition>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of <legacyBold>adStatus</legacyBold> is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise it is not set.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value. When this event is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successful, or to <legacyBold>adStatusErrorsOccurred</legacyBold> if the operation failed. </para>
          <para>Before this event returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
        </definition>
        <definedTerm> <legacyItalic>pCommand</legacyItalic> </definedTerm>
        <definition>
          <para>The <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object that was executed. Contains a <legacyBold>Command</legacyBold> object even when calling <legacyBold>Connection.Execute</legacyBold> or <legacyBold>Recordset.Open</legacyBold> without explicitly creating a <legacyBold>Command</legacyBold>, in which cases the <legacyBold>Command</legacyBold> object is created internally by ADO.</para>
        </definition>
        <definedTerm> <legacyItalic>pRecordset</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object that is the result of the executed command. This <legacyBold>Recordset</legacyBold> may be empty. You should never destroy this Recordset object from within this event handler. Doing so will result in an Access Violation when ADO tries to access an object that no longer exists.</para>
        </definition>
        <definedTerm> <legacyItalic>pConnection</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. The connection over which the operation was executed.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>An <legacyBold>ExecuteComplete</legacyBold> event may occur due to the <legacyBold>Connection.</legacyBold><legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink>, <legacyBold>Command.</legacyBold><legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink>, <legacyBold>Recordset.</legacyBold><legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink>, <legacyBold>Recordset.</legacyBold><legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink>, or <legacyBold>Recordset.</legacyBold><legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink> methods.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>