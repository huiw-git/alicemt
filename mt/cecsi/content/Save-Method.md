---
title: "Save Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5
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
# Save Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Saves the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> in a file or <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
recordset.Save Destination, PersistFormat</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Destination</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Variant</legacyBold> that represents the complete path name of the file where the <legacyBold>Recordset</legacyBold> is to be saved, or a reference to a <legacyBold>Stream</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>PersistFormat</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <link xlink:href="ebe1a2ab-e9f1-43a2-8f94-b190c9613d70">PersistFormatEnum</link> value that specifies the format in which the <legacyBold>Recordset</legacyBold> is to be saved (XML or ADTG). The default value is <legacyBold>adPersistADTG</legacyBold>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link> method can only be invoked on an open <legacyBold>Recordset</legacyBold>. Use the <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link> method to later restore the <legacyBold>Recordset</legacyBold> from <legacyItalic>Destination</legacyItalic>.</para>
      <para>If the <link xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter Property</link> property is in effect for the <legacyBold>Recordset</legacyBold>, then only the rows accessible under the filter are saved. If the <legacyBold>Recordset</legacyBold> is hierarchical, then the current child <legacyBold>Recordset</legacyBold> and its children are saved, including the parent <legacyBold>Recordset</legacyBold>. If the Save method of a child <legacyBold>Recordset</legacyBold> is called, the child and all its children are saved, but the parent is not.</para>
      <para>The first time you save the <legacyBold>Recordset</legacyBold>, it is optional to specify <legacyItalic>Destination</legacyItalic>. If you omit <legacyItalic>Destination</legacyItalic>, a new file will be created with a name set to the value of the Source property of the <legacyBold>Recordset</legacyBold>.</para>
      <para>Omit <legacyItalic>Destination</legacyItalic> when you subsequently call <legacyBold>Save</legacyBold> after the first save, or a run-time error will occur. If you subsequently call <legacyBold>Save</legacyBold> with a new <legacyItalic>Destination</legacyItalic>, the <legacyBold>Recordset</legacyBold> is saved to the new destination. However, the new destination and the original destination will both be open.</para>
      <para>
        <legacyBold>Save</legacyBold> does not close the <legacyBold>Recordset</legacyBold> or <legacyItalic>Destination</legacyItalic>, so you can continue to work with the <legacyBold>Recordset</legacyBold> and save your most recent changes. <legacyItalic>Destination</legacyItalic> remains open until the <legacyBold>Recordset</legacyBold> is closed.</para>
      <para>For reasons of security, the <legacyBold>Save</legacyBold> method permits only the use of low and custom security settings from a script executed by Microsoft Internet Explorer. </para>
      <para>If the <legacyBold>Save</legacyBold> method is called while an asynchronous <legacyBold>Recordset</legacyBold> fetch, execute, or update operation is in progress, then <legacyBold>Save</legacyBold> waits until the asynchronous operation is complete.</para>
      <para>Records are saved beginning with the first row of the <legacyBold>Recordset</legacyBold>. When the <legacyBold>Save</legacyBold> method is finished, the current row position is moved to the first row of the <legacyBold>Recordset</legacyBold>.</para>
      <para>For best results, set the <link xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation Property (ADO)</link> property to <legacyBold>adUseClient</legacyBold> with <legacyBold>Save</legacyBold>. If your provider does not support all of the functionality necessary to save <legacyBold>Recordset</legacyBold> objects, the Cursor Service will provide that functionality.</para>
      <para>When a <legacyBold>Recordset</legacyBold> is persisted with the <legacyBold>CursorLocation</legacyBold> property set to <legacyBold>adUseServer</legacyBold>, the update capability for the <legacyBold>Recordset</legacyBold> is limited. Typically, only single-table updates, insertions, and deletions are allowed (dependant upon provider functionality). The <link xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync Method</link> method is also unavailable in this configuration.</para>
      <alert class="note">
        <para>Saving a <legacyBold>Recordset</legacyBold> with <legacyBold>Fields</legacyBold> of type <legacyBold>adVariant</legacyBold>, <legacyBold>adIDispatch</legacyBold>, or <legacyBold>adIUnknown</legacyBold> is not supported by ADO and can cause unpredictable results.</para>
      </alert>
      <para>Only Filters in the form of Criteria Strings (e.g. OrderDate &gt; '12/31/1999') affect the contents of a persisted <legacyBold>Recordset</legacyBold>. Filters created with an Array of <legacyBold>Bookmarks</legacyBold> or using a value from the <link xlink:href="b22e725e-84bd-4286-a070-290c278c3783">FilterGroupEnum</link> will not affect the contents of the persisted <legacyBold>Recordset</legacyBold>. These rules apply to <legacyBold>Recordset</legacyBold>s created with either client-side or server-side cursors.</para>
      <para>Because the <legacyItalic>Destination</legacyItalic> parameter can accept any object that supports the OLE DB IStream interface, you can save a <legacyBold>Recordset</legacyBold> directly to the ASP Response object. For more details, please see the <legacyBold>XML Recordset Persistence Scenario</legacyBold>.</para>
      <para>You can also save a <legacyBold>Recordset</legacyBold> in XML format to an instance of an MSXML DOM object, as is shown in the following Visual Basic code:</para>
      <code>Dim xDOM As New MSXML.DOMDocument
Dim rsXML As New ADODB.Recordset
Dim sSQL As String, sConn As String

sSQL = "SELECT customerid, companyname, contactname FROM customers"
sConn="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=Northwind.mdb"
rsXML.Open sSQL, sConn
rsXML.Save xDOM, adPersistXML   'Save Recordset directly into a DOM tree.
...</code>
      <alert class="note">
        <para>Two limitations apply when saving hierarchical Recordsets (data shapes) in XML format. You cannot save into XML if the hierarchical <legacyBold>Recordset</legacyBold> contains pending updates, and you cannot save a parameterized hierarchical <legacyBold>Recordset</legacyBold>.</para>
      </alert>
      <para>A <legacyBold>Recordset</legacyBold> saved in XML format is saved using UTF-8 format. When such a file is loaded into an ADO Stream, the Stream object will not attempt to open a <legacyBold>Recordset</legacyBold> from the stream unless the Charset property of the stream is set to the appropriate value for UTF-8 format.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object_ADO</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object_ADO</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ddccdf58-9c57-4c9b-8b7f-0cf193f955fb">Save and Open Methods Example (VB)</link>
<link xlink:href="334ae655-8cac-48e6-8d00-1d28f3436e1e">Save and Open Methods Example (VC++)</link>
<link xlink:href="bc425816-ecf8-4739-b50e-4cd5c60a151c">Save and Open Methods Example (VJ++)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
<link xlink:href="8a8594f2-422b-4d2e-94f8-7fe337445900">SaveToFile Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>