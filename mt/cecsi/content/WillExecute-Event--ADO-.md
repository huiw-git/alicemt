---
title: "WillExecute Event (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: dd755e46-f589-48a3-93a9-51ff998d44b5
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
# WillExecute Event (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>WillExecute</legacyBold> event is called just before a pending command executes on a connection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> that contains an SQL command or a stored procedure name.</para>
        </definition>
        <definedTerm> <legacyItalic>CursorType</legacyItalic> </definedTerm>
        <definition>
          <para>A <link xlink:href="ffc6e245-4471-42ae-84dd-e85bddfce983">CursorTypeEnum</link> that contains the type of cursor for the <legacyBold>Recordset</legacyBold> that will be opened. With this parameter, you can change the cursor to any type during a <legacyBold>Recordset</legacyBold> <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link> operation. <legacyItalic>CursorType</legacyItalic> will be ignored for any other operation.</para>
        </definition>
        <definedTerm> <legacyItalic>LockType </legacyItalic></definedTerm>
        <definition>
          <para>A <link xlink:href="d2894eaf-4450-4ace-aa51-c8b875fd3010">LockTypeEnum</link> that contains the lock type for the <legacyBold>Recordset</legacyBold> that will be opened. With this parameter, you can change the lock to any type during a <legacyBold>Recordset</legacyBold> <legacyBold>Open</legacyBold> operation. <legacyItalic>LockType</legacyItalic> will be ignored for any other operation.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Long</legacyBold> value that indicates options that can be used to execute the command or open the <legacyBold>Recordset</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <link xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</link> status value that may be <legacyBold>adStatusCantDeny</legacyBold> or <legacyBold>adStatusOK</legacyBold> when this event is called. If it is <legacyBold>adStatusCantDeny</legacyBold>, this event may not request cancellation of the pending operation.</para>
        </definition>
        <definedTerm> <legacyItalic>pCommand </legacyItalic></definedTerm>
        <definition>
          <para>The <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object_ADO</link> object for which this event notification applies.</para>
        </definition>
        <definedTerm> <legacyItalic>pRecordset </legacyItalic></definedTerm>
        <definition>
          <para>The <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object_ADO</link> object for which this event notification applies.</para>
        </definition>
        <definedTerm> <legacyItalic>pConnection </legacyItalic></definedTerm>
        <definition>
          <para>The <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object_ADO</link> object for which this event notification applies.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>WillExecute</legacyBold> event may occur due to a Connection.  <link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>, <link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>, or <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link> method The <legacyItalic>pConnection</legacyItalic> parameter should always contain a valid reference to a <legacyBold>Connection</legacyBold> object. If the event is due to <legacyBold>Connection.Execute</legacyBold>, the <legacyItalic>pRecordset</legacyItalic> and <legacyItalic>pCommand</legacyItalic> parameters are set to <legacyBold>Nothing</legacyBold>. If the event is due to <legacyBold>Recordset.Open</legacyBold>, the <legacyItalic>pRecordset</legacyItalic> parameter will reference the <legacyBold>Recordset</legacyBold> object and the <legacyItalic>pCommand</legacyItalic> parameter is set to <legacyBold>Nothing</legacyBold>. If the event is due to <legacyBold>Command.Execute</legacyBold>, the <legacyItalic>pCommand</legacyItalic> parameter will reference the <legacyBold>Command</legacyBold> object and the <legacyItalic>pRecordset</legacyItalic> parameter is set to <legacyBold>Nothing</legacyBold>.</para>
      <para>
        <legacyBold>WillExecute</legacyBold> allows you to examine and modify the pending execution parameters. This event may return a request that the pending command be canceled.</para>
      <alert class="note">
        <para>If the original source for a <legacyBold>Command</legacyBold> is a stream specified by the <link xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream Property (ADO)</link> property, assigning a new string to the <legacyBold>WillExecute</legacyBold> <legacyItalic>Source</legacyItalic> parameter changes the source of the <legacyBold>Command</legacyBold>. The <legacyBold>CommandStream</legacyBold> property will be cleared and the <link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property (ADO)</link> property will be updated with the new source. The original stream specified by <legacyBold>CommandStream</legacyBold> will be released and cannot be accessed.</para>
      </alert>
      <para>If the dialect of the new source string differs from the original setting of the <link xlink:href="329c3a71-ba88-4009-b04f-2f52195a5957">Dialect Property</link> property (which corresponded to the <legacyBold>CommandStream</legacyBold>), the correct dialect must be specified by setting the <legacyBold>Dialect</legacyBold> property of the command object referenced by <legacyItalic>pCommand</legacyItalic>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">ADO Events Model Example (VC++)</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object_ADO</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>