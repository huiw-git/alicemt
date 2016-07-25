---
title: "Resync Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
caps.latest.revision: 12
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
# Resync Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Refreshes the data in the current <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, or <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object, from the underlying database.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Recordset</parameterReference><legacyBold>.Resync</legacyBold> <parameterReference>AffectRecords, ResyncValues</parameterReference> <parameterReference>Record.Fields</parameterReference><legacyBold>.Resync</legacyBold> <parameterReference>ResyncValues</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>AffectRecords</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. An <legacyLink xlink:href="1ab921a0-6c57-43b4-9291-701b2599f3e8">AffectEnum</legacyLink> value that determines how many records the <legacyBold>Resync</legacyBold> method will affect. The default value is <legacyBold>adAffectAll</legacyBold>. This value is not available with the <legacyBold>Resync</legacyBold> method of the <legacyBold>Fields</legacyBold> collection of a <legacyBold>Record</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>ResyncValues</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="d3df2c90-e570-4c40-a79a-25b3448a009c">ResyncEnum</legacyLink> value that specifies whether underlying values are overwritten. The default value is <legacyBold>adResyncAllValues</legacyBold>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content />
    <sections>
      <section>
        <title>Recordset</title>
        <content>
          <para>Use the <legacyBold>Resync</legacyBold> method to resynchronize records in the current <legacyBold>Recordset</legacyBold> with the underlying database. This is useful if you are using either a static or forward-only cursor, but you want to see any changes in the underlying database.</para>
          <para>If you set the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold>, <legacyBold>Resync</legacyBold> is only available for non-read-only <legacyBold>Recordset</legacyBold> objects.</para>
          <para>Unlike the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method, the <legacyBold>Resync</legacyBold> method does not re-execute the <legacyBold>Recordset</legacyBold> object's underlying command. New records in the underlying database will not be visible.</para>
          <para>If the attempt to resynchronize fails because of a conflict with the underlying data (for example, a record has been deleted by another user), the provider returns warnings to the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection and a run-time error occurs. Use the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property (<legacyBold>adFilterConflictingRecords</legacyBold>) and the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property to locate records with conflicts.</para>
          <para>If the <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink> and <legacyLink xlink:href="4e2bb601-0fe8-4d61-b00e-38341d85a6bb">Resync Command</legacyLink> dynamic properties are set, and the <legacyBold>Recordset</legacyBold> is the result of executing a JOIN operation on multiple tables, then the <legacyBold>Resync</legacyBold> method will execute the command given in the <legacyBold>Resync Command</legacyBold> property only on the table named in the <legacyBold>Unique Table</legacyBold> property.</para>
        </content>
      </section>
      <section>
        <title>Fields</title>
        <content>
          <para>Use the <legacyBold>Resync</legacyBold> method to resynchronize the values of the <legacyBold>Fields</legacyBold> collection of a <legacyBold>Record</legacyBold> object with the underlying data source. The <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property is not affected by this method.</para>
          <para>If <legacyItalic>ResyncValues</legacyItalic> is set to <legacyBold>adResyncAllValues</legacyBold> (the default value), the <legacyLink xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue</legacyLink>, <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink>, and <legacyLink xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue</legacyLink> properties of <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects in the collection are synchronized. If <legacyItalic>ResyncValues</legacyItalic> is set to <legacyBold>adResyncUnderlyingValues</legacyBold>, only the <legacyBold>UnderlyingValue</legacyBold> property is synchronized.</para>
          <para>The value of the <legacyBold>Status</legacyBold> property for each <legacyBold>Field</legacyBold> object at the time of the call also affects the behavior of <legacyBold>Resync</legacyBold>. For <legacyBold>Field</legacyBold> objects that have <legacyBold>Status</legacyBold> values of <legacyBold>adFieldPendingUnknown</legacyBold> or <legacyBold>adFieldPendingInsert</legacyBold>, <legacyBold>Resync</legacyBold> has no effect. For <legacyBold>Status</legacyBold> values of <legacyBold>adFieldPendingChange</legacyBold> or <legacyBold>adFieldPendingDelete</legacyBold>, <legacyBold>Resync</legacyBold> synchronizes data values for fields that still exist at the data source.</para>
          <para>
            <legacyBold>Resync</legacyBold> will not modify <legacyBold>Status</legacyBold> values of <legacyBold>Field</legacyBold> objects unless an error occurs when <legacyBold>Resync</legacyBold> is called. For example, if the field no longer exists, the provider will return an appropriate <legacyBold>Status</legacyBold> value for the <legacyBold>Field</legacyBold> object, such as <legacyBold>adFieldDoesNotExist</legacyBold>. Returned <legacyBold>Status</legacyBold> values can be logically combined within the value of the <legacyBold>Status</legacyBold> property.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ab95315c-fe15-458c-9e0c-937ae5596592">Visual Basic Example</link>
<link xlink:href="d34dfd26-9ca7-4c9c-a918-396f05fecca9">Visual C++ Example</link>
<link xlink:href="0ef0ed20-83ac-4047-9294-506fd82f7201">Visual J++ Example</link>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>