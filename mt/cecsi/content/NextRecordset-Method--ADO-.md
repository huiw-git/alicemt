---
title: "NextRecordset Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
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
# NextRecordset Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Clears the current <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object and returns the next <legacyBold>Recordset</legacyBold> by advancing through a series of commands.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set</legacyBold> <parameterReference>recordset2</parameterReference> = <parameterReference>recordset1</parameterReference><legacyBold>.NextRecordset(</legacyBold><parameterReference>RecordsAffected </parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyBold>Recordset</legacyBold> object. In the syntax model, <legacyItalic>recordset1</legacyItalic> and <legacyItalic>recordset2</legacyItalic> can be the same <legacyBold>Recordset</legacyBold> object, or you can use separate objects. When using separate <legacyBold>Recordset</legacyBold> objects, resetting the <legacyBold>ActiveConnection</legacyBold> property on the original <legacyBold>Recordset</legacyBold> (<legacyItalic>recordset1</legacyItalic>) after <legacyBold>NextRecordset</legacyBold> has been called will generate an error. </para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>RecordsAffected</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Long</languageKeyword> variable to which the provider returns the number of records that the current operation affected.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>This parameter only returns the number of records affected by an operation; it does not return a count of records from a select statement used to generate the <legacyBold>Recordset</legacyBold>.</para>
      </alert>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>NextRecordset</legacyBold> method to return the results of the next command in a compound command statement or of a stored procedure that returns multiple results. If you open a <legacyBold>Recordset</legacyBold> object based on a compound command statement (for example, "SELECT * FROM table1;SELECT * FROM table2") using the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method on a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> or the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method on a <legacyBold>Recordset</legacyBold>, ADO executes only the first command and returns the results to <legacyItalic>recordset</legacyItalic>. To access the results of subsequent commands in the statement, call the <legacyBold>NextRecordset</legacyBold> method.</para>
      <para>As long as there are additional results and the <legacyBold>Recordset</legacyBold> containing the compound statements is not disconnected or marshaled across process boundaries, the <legacyBold>NextRecordset</legacyBold> method will continue to return <legacyBold>Recordset</legacyBold> objects. If a row-returning command executes successfully but returns no records, the returned <legacyBold>Recordset</legacyBold> object will be open but empty. Test for this case by verifying that the <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF</legacyLink> and <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> properties are both <legacyBold>True</legacyBold>. If a non–row-returning command executes successfully, the returned <legacyBold>Recordset</legacyBold> object will be closed, which you can verify by testing the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property on the <legacyBold>Recordset</legacyBold>. When there are no more results, <legacyItalic>recordset</legacyItalic> will be set to <legacyItalic>Nothing</legacyItalic>.</para>
      <para>The <legacyBold>NextRecordset</legacyBold> method is not available on a disconnected <legacyBold>Recordset</legacyBold> object, where <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> has been set to <legacyBold>Nothing</legacyBold> (in Microsoft Visual Basic) or NULL (in other languages).</para>
      <para>If an edit is in progress while in immediate update mode, calling the <legacyBold>NextRecordset</legacyBold> method generates an error; call the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> or <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method first.</para>
      <para>To pass parameters for more than one command in the compound statement by filling the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection, or by passing an array with the original <legacyBold>Open</legacyBold> or <legacyBold>Execute</legacyBold> call, the parameters must be in the same order in the collection or array as their respective commands in the command series. You must finish reading all the results before reading output parameter values.</para>
      <para>Your OLE DB provider determines when each command command in a compound statement is executed. The <legacyLink xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">Microsoft OLE DB Provider for SQL Server</legacyLink>, for example, executes all commands in a batch upon receiving the compound statement. The resulting <legacyBold>Recordsets</legacyBold> are simply returned when you call <legacyBold>NextRecordset</legacyBold>.</para>
      <para>However, other providers may execute the next command in a statement only after NextRecordset is called. For these providers, if you explicitly close the <legacyBold>Recordset</legacyBold> object before stepping through the entire command statement, ADO never executes the remaining commands.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b14806da-80d9-4da4-bb87-f558b36a6ac0">Visual Basic Example</link>
<link xlink:href="8bb72817-0cf5-4ce9-9fb8-043c89da941c">Visual C++ Example</link>
<link xlink:href="7948eefb-f5cc-4e74-b2f4-39033b46243d">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>