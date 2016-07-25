---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a61a01a7-5b33-4150-9126-21dfa63654cb
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
# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Moves to the first, last, next, or previous record in a specified <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object and makes that record the current record.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference><legacyBold>.</legacyBold>{<legacyBold>MoveFirst</legacyBold> | <legacyBold>MoveLast</legacyBold> | <legacyBold>MoveNext</legacyBold> | <legacyBold>MovePrevious</legacyBold>}</legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>MoveFirst</legacyBold> method to move the current record position to the first record in the <legacyBold>Recordset</legacyBold>.</para>
      <para>Use the <legacyBold>MoveLast</legacyBold> method to move the current record position to the last record in the <legacyBold>Recordset</legacyBold>. The <legacyBold>Recordset</legacyBold> object must support bookmarks or backward cursor movement; otherwise, the method call will generate an error.</para>
      <para>A call to either <legacyBold>MoveFirst</legacyBold> or <legacyBold>MoveLast</legacyBold> when the <legacyBold>Recordset</legacyBold> is empty (both <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> are True) generates an error.</para>
      <para>Use the <legacyBold>MoveNext</legacyBold> method to move the current record position one record forward (toward the bottom of the <legacyBold>Recordset</legacyBold>). If the last record is the current record and you call the <legacyBold>MoveNext</legacyBold> method, ADO sets the current record to the position after the last record in the <legacyBold>Recordset</legacyBold> (<legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> is <legacyBold>True</legacyBold>). An attempt to move forward when the <legacyBold>EOF</legacyBold> property is already <legacyBold>True</legacyBold> generates an error.</para>
      <para>In ADO 2.5 and later, when the <legacyBold>Recordset</legacyBold> has been filtered or sorted and the data of the current record is changed, calling the <legacyBold>MoveNext</legacyBold> method moves the cursor two records forward from the current record. This is because when the current record is changed, the next record becomes the new current record. Calling <legacyBold>MoveNext</legacyBold> after the change moves the cursor one record forward from the new current record. This is different from the behavior in ADO 2.1 and earlier. In these earlier versions, changing the data of a current record in the sorted or filtered <legacyBold>Recordset</legacyBold> does not change the position of the current record, and <legacyBold>MoveNext</legacyBold> moves the cursor to the next record immediately after the current record.</para>
      <para>Use the <legacyBold>MovePrevious</legacyBold> method to move the current record position one record backward (toward the top of the <legacyBold>Recordset</legacyBold>). The <legacyBold>Recordset</legacyBold> object must support bookmarks or backward cursor movement; otherwise, the method call will generate an error. If the first record is the current record and you call the <legacyBold>MovePrevious</legacyBold> method, ADO sets the current record to the position before the first record in the <legacyBold>Recordset</legacyBold> (<legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF</legacyLink> is <legacyBold>True</legacyBold>). An attempt to move backward when the <legacyBold>BOF</legacyBold> property is already <legacyBold>True</legacyBold> generates an error. If the <legacyBold>Recordset</legacyBold> object does not support either bookmarks or backward cursor movement, the <legacyBold>MovePrevious</legacyBold> method will generate an error.</para>
      <para>If the <legacyBold>Recordset</legacyBold> is forward only and you want to support both forward and backward scrolling, you can use the <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property to create a record cache that will support backward cursor movement through the <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink> method. Because cached records are loaded into memory, you should avoid caching more records than is necessary. You can call the <legacyBold>MoveFirst</legacyBold> method in a forward-only <legacyBold>Recordset</legacyBold> object; doing so may cause the provider to re-execute the command that generated the <legacyBold>Recordset</legacyBold> object.</para>
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
<link xlink:href="31d3b083-c677-423e-8d26-a212eaeea281">Visual Basic Example</link>
<link xlink:href="911aa1dd-2786-4f34-992c-bb2fbdabcbdf">VBScript Example</link>
<link xlink:href="7f8aea7b-9183-4b29-8ac0-a393ed2e8bd5">Visual C++ Example</link>
<link xlink:href="d2db8a95-3072-4007-a127-44376405a67e">Visual J++ Example</link>
<link xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move Method</link>
<link xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)</link>
<link xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>