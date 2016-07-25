---
title: "Move Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 13fe9381-d00b-4f4a-9162-83c3f21b3837
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
# Move Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Moves the position of the current record in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference><legacyBold>.Move</legacyBold> <parameterReference>NumRecords</parameterReference><legacyBold>, </legacyBold><parameterReference>Start</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>NumRecords</legacyItalic> </definedTerm>
        <definition>
          <para>A signed <languageKeyword>Long</languageKeyword> expression that specifies the number of records that the current record position moves.</para>
        </definition>
        <definedTerm> <legacyItalic>Start</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value or <languageKeyword>Variant</languageKeyword> that evaluates to a bookmark. You can also use a <legacyLink xlink:href="55d273c4-ccee-48ef-ba90-8893d04313c8">BookmarkEnum</legacyLink> value.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <unmanagedCodeEntityReference>Move</unmanagedCodeEntityReference> method is supported on all <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> objects.</para>
      <para>If the <legacyItalic>NumRecords</legacyItalic> argument is greater than zero, the current record position moves forward (toward the end of the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>). If <legacyItalic>NumRecords</legacyItalic> is less than zero, the current record position moves backward (toward the beginning of the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>).</para>
      <para>If the <unmanagedCodeEntityReference>Move</unmanagedCodeEntityReference> call would move the current record position to a point before the first record, ADO sets the current record to the position before the first record in the recordset (<legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF</legacyLink> is <languageKeyword>True</languageKeyword>). An attempt to move backward when the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> property is already <languageKeyword>True</languageKeyword> generates an error.</para>
      <para>If the <unmanagedCodeEntityReference>Move</unmanagedCodeEntityReference> call would move the current record position to a point after the last record, ADO sets the current record to the position after the last record in the recordset (<legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> is <languageKeyword>True</languageKeyword>). An attempt to move forward when the <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> property is already <languageKeyword>True</languageKeyword> generates an error.</para>
      <para>Calling the <unmanagedCodeEntityReference>Move</unmanagedCodeEntityReference> method from an empty <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object generates an error.</para>
      <para>If you pass the <legacyItalic>Start</legacyItalic> argument, the move is relative to the record with this bookmark, assuming the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports bookmarks. If not specified, the move is relative to the current record.</para>
      <para>If you are using the <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property to locally cache records from the provider, passing a <legacyItalic>NumRecords</legacyItalic> argument that moves the current record position outside the current group of cached records forces ADO to retrieve a new group of records, starting from the destination record. The <unmanagedCodeEntityReference>CacheSize</unmanagedCodeEntityReference> property determines the size of the newly retrieved group, and the destination record is the first record retrieved.</para>
      <para>If the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object is forward only, a user can still pass a <legacyItalic>NumRecords</legacyItalic> argument less than zero, provided the destination is within the current set of cached records. If the <unmanagedCodeEntityReference>Move</unmanagedCodeEntityReference> call would move the current record position to a record before the first cached record, an error will occur. Thus, you can use a record cache that supports full scrolling over a provider that supports only forward scrolling. Because cached records are loaded into memory, you should avoid caching more records than are necessary. Even if a forward-only <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports backward moves in this way, calling the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink> method on any forward-only <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object will still generate an error.</para>
      <alert class="note">
        <para>Support for moving backwards in a forward-only <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is not predictable, depending upon your provider. If the current record has been positioned after the last record in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>Move</unmanagedCodeEntityReference> backwards may not result in the correct current position.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="55eb797a-0205-40d2-a797-55b216d1d3bb">Visual Basic Example</link>
<link xlink:href="29ec4b95-8986-4970-943f-3da3ecb207a2">VBScript Example</link>
<link xlink:href="0e08af60-f668-4092-8b6a-9e8b6db90448">Visual C++ Example</link>
<link xlink:href="b29ddb8c-ceb3-4aad-a240-8030462fceba">Visual J++ Example</link>
<link xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods</link>
<link xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)</link>
<link xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>