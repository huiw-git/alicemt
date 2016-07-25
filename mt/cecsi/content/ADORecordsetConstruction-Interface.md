---
title: "ADORecordsetConstruction Interface"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
caps.latest.revision: 8
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
# ADORecordsetConstruction Interface
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>ADORecordsetConstruction</legacyBold> interface is used to construct an ADO <legacyBold>Recordset</legacyBold> object from an OLE DB <legacyBold>Rowset</legacyBold> object in a C/C++ application. </para>
    <para>This interface supports the following properties:</para>
  </introduction>
  <section>
    <title>Properties</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="8aa90cb0-f588-4141-9dc9-3b22918394ee">Chapter</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Read/Write.
Gets/sets an OLE DB <legacyBold>Chapter</legacyBold> object from/on this ADO <legacyBold>Recordset</legacyBold> object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="9d068fed-39bf-4842-afc3-686a2af2145d">RowPosition</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Read/Write.
Gets/sets an OLE DB <legacyBold>RowPosition</legacyBold> object from/on this ADO <legacyBold>Recordset</legacyBold> object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="7d359294-4ff2-47e0-8111-0c221b24d80e">Rowset</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Read/Write.
Gets/sets an OLE DB <legacyBold>Rowset</legacyBold> object from/on this ADO <legacyBold>Recordset</legacyBold> object.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Methods</title>
    <content>
      <para>None.</para>
    </content>
  </section>
  <section>
    <title>Events</title>
    <content>
      <para>None.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Given an OLE DB <legacyBold>Rowset</legacyBold> object (<codeInline>pRowset</codeInline>), the construction of an ADO <legacyBold>Recordset</legacyBold> object (<codeInline>adoRs</codeInline>) amounts to the following three basic operations:

</para>
      <list class="ordered">
        <listItem>
          <para>Create an ADO <legacyBold>Recordset</legacyBold> object:
</para>
          <code>Recordset20Ptr adoRs;
adoRs.CreateInstance(__uuidof(Recordset));</code>
        </listItem>
        <listItem>
          <para>Query the <legacyBold>IADORecordsetConstruction</legacyBold> interface on the <legacyBold>Recordset</legacyBold> object:
</para>
          <code>adoRecordsetConstructionPtr adoRsConstruct=NULL;
adoRs-&gt;QueryInterface(__uuidof(ADORecordsetConstruction),
                     (void**)&amp;adoRsConstruct);</code>
        </listItem>
        <listItem>
          <para>Call the <codeInline>IADORecordsetConstruction::put_Rowset</codeInline> property method to set the OLE DB <codeInline>Rowset</codeInline> object on the ADO <codeInline>Recordset</codeInline> object:
</para>
          <code>IUnknown *pUnk=NULL;
pRowset-&gt;QueryInterface(IID_IUnknown, (void**)&amp;pUnk);
adoRsConstruct-&gt;put_Rowset(pUnk);</code>
        </listItem>
      </list>
      <para>The resultant <codeInline>adoRs</codeInline> object now represents the ADO <legacyBold>Recordset</legacyBold> object constructed from the OLE DB <legacyBold>Rowset</legacyBold> object.</para>
      <para>You can also construct an ADO <legacyBold>Recordset</legacyBold> object from an OLE DB <legacyBold>Chapter</legacyBold> or <legacyBold>RowPosition</legacyBold> object.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Requirements</title>
    <content>
      <para>
        <legacyBold>Version:</legacyBold> ADO 2.0 and later</para>
      <para>
        <legacyBold>Library:</legacyBold> msado15.dll</para>
      <para>
        <legacyBold>UUID:</legacyBold> 00000283-0000-0010-8000-00AA006D2EA4</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="7d359294-4ff2-47e0-8111-0c221b24d80e">Rowset Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>