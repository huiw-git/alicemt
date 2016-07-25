---
title: "Clone Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
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
# Clone Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates a duplicate <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object from an existing <legacyBold>Recordset</legacyBold> object. Optionally, specifies that the clone be read-only.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set</legacyBold> <parameterReference>rstDuplicate</parameterReference> = <parameterReference>rstOriginal</parameterReference>.<legacyBold>Clone (</legacyBold><parameterReference>LockType</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyBold>Recordset</legacyBold> object reference.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>rstDuplicate</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that identifies the duplicate <legacyBold>Recordset</legacyBold> object to be created.</para>
        </definition>
        <definedTerm> <legacyItalic>rstOriginal</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that identifies the <legacyBold>Recordset</legacyBold> object to be duplicated.</para>
        </definition>
        <definedTerm> <legacyItalic>LockType</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="d2894eaf-4450-4ace-aa51-c8b875fd3010">LockTypeEnum</legacyLink> value that specifies either the lock type of the original <legacyBold>Recordset</legacyBold>, or a read-only <legacyBold>Recordset</legacyBold>. Valid values are <legacyBold>adLockUnspecified</legacyBold> or <legacyBold>adLockReadOnly</legacyBold>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Clone</legacyBold> method to create multiple, duplicate <legacyBold>Recordset</legacyBold> objects, especially if you want to maintain more than one current record in a given set of records. Using the <legacyBold>Clone</legacyBold> method is more efficient than creating and opening a new <legacyBold>Recordset</legacyBold> object that uses the same definition as the original.</para>
      <para>The <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property of the original <legacyBold>Recordset</legacyBold>, if any, will not be applied to the clone. Set the <legacyBold>Filter</legacyBold> property of the new <legacyBold>Recordset</legacyBold> to filter the results. The simplest way to copy any existing <legacyBold>Filter</legacyBold> value is to assign it directly, as follows.</para>
      <code>rsNew.Filter = rsOriginal.Filter</code>
      <para>The current record of a newly created clone is set to the first record.</para>
      <para>Changes you make to one <legacyBold>Recordset</legacyBold> object are visible in all of its clones regardless of cursor type. However, after you execute <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> on the original <legacyBold>Recordset</legacyBold>, the clones will no longer be synchronized to the original.</para>
      <para>Closing the original <legacyBold>Recordset</legacyBold> does not close its copies, nor does closing a copy close the original or any of the other copies.</para>
      <para>You can only clone a <legacyBold>Recordset</legacyBold> object that supports bookmarks. Bookmark values are interchangeable; that is, a bookmark reference from one <legacyBold>Recordset</legacyBold> object refers to the same record in any of its clones.</para>
      <para>Some <legacyBold>Recordset</legacyBold> events that are triggered will also occur in all <legacyBold>Recordset</legacyBold> clones. However, because the current record can differ between cloned <legacyBold>Recordsets</legacyBold>, the events may not be valid for the clone. For example, if you change a value of a field, a <legacyLink xlink:href="3e49fb89-c45b-4d39-823e-3cc887c59b37">WillChangeField</legacyLink> event will occur in the changed <legacyBold>Recordset</legacyBold> and in all clones. The <legacyItalic>Fields</legacyItalic> parameter of the <legacyBold>WillChangeField</legacyBold> event of a cloned <legacyBold>Recordset</legacyBold> (where the change was not made) will refer to the fields of the current record of the clone, which may be a different record than the current record of the original <legacyBold>Recordset</legacyBold> where the change occurred.</para>
      <para>The following table provides a full listing of all <legacyBold>Recordset</legacyBold> events. It indicates whether they are valid and triggered for any recordset clones generated by using the <legacyBold>Clone</legacyBold> method.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Event</para>
            </TD>
            <TD>
              <para>Triggered in clones?</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="475de5e2-f634-4954-9edf-0027a6ba38d6">EndOfRecordset</legacyLink>             </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a28d3858-566c-468d-b070-d1de4339fbea">FetchComplete</legacyLink>             </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="301716fd-81fc-40eb-8a04-221ef7ab410e">FetchProgress</legacyLink>             </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3e49fb89-c45b-4d39-823e-3cc887c59b37">FieldChangeComplete</legacyLink>             </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">MoveComplete</legacyLink>             </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="cbc369fd-63af-4a7d-96ae-efa91b78ca69">RecordChangeComplete</legacyLink>             </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">RecordsetChangeComplete</legacyLink>             </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3e49fb89-c45b-4d39-823e-3cc887c59b37">WillChangeField</legacyLink>             </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="cbc369fd-63af-4a7d-96ae-efa91b78ca69">WillChangeRecord</legacyLink>             </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">WillChangeRecordset</legacyLink>             </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">WillMove</legacyLink>             </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
        </tbody>
      </table>
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
<link xlink:href="64cb1753-e074-4a2d-8b74-7c35f3f6f64d">Visual Basic Example</link>
<link xlink:href="36b96e3d-8cb0-4b79-bd93-ea5e0eb5679f">VBScript Example</link>
<link xlink:href="7ac96c1d-d0d8-4bf8-b165-533818d0f590">Visual C++ Example</link>
<link xlink:href="6b699f2b-e5c7-4584-ab25-663a9243d30e">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>