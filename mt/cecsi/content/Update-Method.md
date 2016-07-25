---
title: "Update Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
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
# Update Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Saves any changes you make to the current row of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, or the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference><legacyBold>.Update</legacyBold> <parameterReference>Fields</parameterReference><legacyBold>,</legacyBold> <parameterReference>Values</parameterReference>
<parameterReference>record.Fields</parameterReference><legacyBold>.Update</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Fields</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Variant</legacyBold> that represents a single name, or a <legacyBold>Variant</legacyBold> array that represents names or ordinal positions of the field or fields you wish to modify.</para>
        </definition>
        <definedTerm> <legacyItalic>Values</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Variant</legacyBold> that represents a single value, or a <legacyBold>Variant</legacyBold> array that represents values for the field or fields in the new record.</para>
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
          <para>Use the <legacyBold>Update</legacyBold> method to save any changes you make to the current record of a <legacyBold>Recordset</legacyBold> object since calling the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method or since changing any field values in an existing record. The <legacyBold>Recordset</legacyBold> object must support updates.</para>
          <para>To set field values, do one of the following:  </para>
          <list class="bullet">
            <listItem>
              <para>Assign values to a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object's <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property and call the <legacyBold>Update</legacyBold> method.</para>
            </listItem>
            <listItem>
              <para>Pass a field name and a value as arguments with the <legacyBold>Update</legacyBold> call.</para>
            </listItem>
            <listItem>
              <para>Pass an array of field names and an array of values with the <legacyBold>Update</legacyBold> call.</para>
            </listItem>
          </list>
          <para>When you use arrays of fields and values, there must be an equal number of elements in both arrays. Also, the order of field names must match the order of field values. If the number and order of fields and values do not match, an error occurs.</para>
          <para>If the <legacyBold>Recordset</legacyBold> object supports batch updating, you can cache multiple changes to one or more records locally until you call the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method. If you are editing the current record or adding a new record when you call the <legacyBold>UpdateBatch</legacyBold> method, ADO will automatically call the <legacyBold>Update</legacyBold> method to save any pending changes to the current record before transmitting the batched changes to the provider.</para>
          <para>If you move from the record you are adding or editing before calling the <legacyBold>Update</legacyBold> method, ADO will automatically call <legacyBold>Update</legacyBold> to save the changes. You must call the <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method if you want to cancel any changes made to the current record or discard a newly added record.</para>
          <para>The current record remains current after you call the <legacyBold>Update</legacyBold> method.</para>
        </content>
      </section>
      <section>
        <title>Record</title>
        <content>
          <para>The <legacyBold>Update</legacyBold> method finalizes additions, deletions, and updates to fields in the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyBold>Record</legacyBold> object.</para>
          <para>For example, fields deleted with the <legacyBold>Delete</legacyBold> method are marked for deletion immediately but remain in the collection. The <legacyBold>Update</legacyBold> method must be called to actually delete these fields from the provider's collection.</para>
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
<link xlink:href="55bedd08-7440-4da4-b854-4ac9ef2fdedb">Visual Basic Example</link>
<link xlink:href="cc59d23a-2f38-42f9-8b65-ed89009e87ec">Visual C++ Example</link>
<link xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew Method</link>
<link xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate Method</link>
<link xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode Property</link>
<link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>