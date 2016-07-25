---
title: "AddNew Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
caps.latest.revision: 13
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
# AddNew Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates a new record for an updatable <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
recordset.AddNew FieldList, Values</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>recordset</legacyItalic>
        </definedTerm>
        <definition>
          <para>A <legacyBold>Recordset</legacyBold> object.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FieldList</legacyItalic>
        </definedTerm>
        <definition>
          <para>Optional. A single name, or an array of names or ordinal positions of the fields in the new record.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Values</legacyItalic>
        </definedTerm>
        <definition>
          <para>Optional. A single value, or an array of values for the fields in the new record. If <legacyItalic>Fieldlist </legacyItalic>is an array, <legacyItalic>Values</legacyItalic> must also be an array with the same number of members; otherwise, an error occurs. The order of field names must match the order of field values in each array.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>AddNew</legacyBold> method to create and initialize a new record. Use the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method with <legacyBold>adAddNew</legacyBold> (a <legacyLink xlink:href="4e10cda7-ce81-4466-94c2-844d38191cf1">CursorOptionEnum</legacyLink> value) to verify whether you can add records to the current <legacyBold>Recordset</legacyBold> object.</para>
      <para>After you call the <legacyBold>AddNew</legacyBold> method, the new record becomes the current record and remains current after you call the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method. Since the new record is appended to the <legacyBold>Recordset</legacyBold>, a call to <legacyBold>MoveNext</legacyBold> following the Update will move past the end of the <legacyBold>Recordset</legacyBold>, making <legacyBold>EOF</legacyBold> True. If the <legacyBold>Recordset</legacyBold> object does not support bookmarks, you may not be able to access the new record once you move to another record. Depending on your cursor type, you may need to call the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method to make the new record accessible.</para>
      <para>If you call <legacyBold>AddNew</legacyBold> while editing the current record or while adding a new record, ADO calls the <legacyBold>Update</legacyBold> method to save any changes and then creates the new record.</para>
      <para>The behavior of the <legacyBold>AddNew</legacyBold> method depends on the updating mode of the <legacyBold>Recordset</legacyBold> object and whether you pass the <legacyItalic>Fieldlist</legacyItalic> and <legacyItalic>Values</legacyItalic> arguments.</para>
      <para>In <legacyItalic>immediate update mode</legacyItalic> (in which the provider writes changes to the underlying data source once you call the <legacyBold>Update</legacyBold> method), calling the <legacyBold>AddNew</legacyBold> method without arguments sets the <legacyLink xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode</legacyLink> property to <legacyBold>adEditAdd</legacyBold> (an <legacyLink xlink:href="45d54b6e-db2c-4553-9fd0-528147d6da2f">EditModeEnum</legacyLink> value). The provider caches any field value changes locally. Calling the <legacyBold>Update</legacyBold> method posts the new record to the database and resets the <legacyBold>EditMode</legacyBold> property to <legacyBold>adEditNone</legacyBold> (an <legacyBold>EditModeEnum</legacyBold> value). If you pass the <legacyItalic>Fieldlist</legacyItalic> and <legacyItalic>Values</legacyItalic> arguments, ADO immediately posts the new record to the database (no <legacyBold>Update</legacyBold> call is necessary); the <legacyBold>EditMode</legacyBold> property value does not change (<legacyBold>adEditNone</legacyBold>).</para>
      <para>In <legacyItalic>batch update mode</legacyItalic> (in which the provider caches multiple changes and writes them to the underlying data source only when you call the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method), calling the <legacyBold>AddNew</legacyBold> method without arguments sets the <legacyBold>EditMode</legacyBold> property to <legacyBold>adEditAdd</legacyBold>. The provider caches any field value changes locally. Calling the <legacyBold>Update</legacyBold> method adds the new record to the current <legacyBold>Recordset</legacyBold>, but the provider does not post the changes to the underlying database, or reset the <legacyBold>EditMode</legacyBold> to <legacyBold>adEditNone</legacyBold>, until you call the <legacyBold>UpdateBatch</legacyBold> method. If you pass the <legacyItalic>Fieldlist</legacyItalic> and <legacyItalic>Values</legacyItalic> arguments, ADO sends the new record to the provider for storage in a cache and sets the <legacyBold>EditMode</legacyBold> to <legacyBold>adEditAdd</legacyBold>; you need to call the <legacyBold>UpdateBatch</legacyBold> method to post the new record to the underlying database.</para>
    </content>
  </languageReferenceRemarks>
  <codeExample>
    <description>
      <content>
        <para>The following example shows how to use the AddNew method with the field list and value list included, to see how to include the field list and value list as arrays.</para>
      </content>
    </description>
    <code>create table aa1 (intf int, charf char(10))
insert into aa1 values (2, 'aa')

Dim cn As New adodb.Connection
Dim rs As New adodb.Recordset
Dim cmd As New adodb.Command

cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"

cn.Open
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic

Dim fieldsArray(1) As Variant
fieldsArray(0) = "intf"
fieldsArray(1) = "charf"
Dim values(1) As Variant
values(0) = 4
values(1) = "as"
rs.AddNew fieldsArray, values
rs.Update</code>
  </codeExample>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d439e097-65f3-471d-8799-5a1263beb3c1">Visual Basic Example</link>
<link xlink:href="dcdcaf0a-b9b0-4d81-8728-43c38c4c853b">VBScript Example</link>
<link xlink:href="9cc8774b-6711-4837-b442-959eaf79343e">Visual C++ Example</link>
<link xlink:href="12856ffb-8645-4fad-b51f-2c2967677c01">Visual J++ Example</link>
<link xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate Method</link>
<link xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode Property</link>
<link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
<link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
<link xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update Method</link>
<link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>