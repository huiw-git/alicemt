---
title: "ADOStreamConstruction Interface"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
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
# ADOStreamConstruction Interface
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>ADOStreamConstruction</legacyBold> interface is used to construct an ADO <legacyBold>Stream</legacyBold> object from an OLE DB <legacyBold>IStream</legacyBold> object in a C/C++ application. </para>
  </introduction>
  <section>
    <title>Properties</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="4a44f9f6-0265-4c00-8def-d85b6af923b1">Stream</link>
              </para>
            </TD>
            <TD>
              <para>Read/Write. Gets/sets an OLE DB <legacyBold>Stream</legacyBold> object.</para>
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
      <para>Given an OLE DB <legacyBold>IStream</legacyBold> object (<codeInline>pStream</codeInline>), the construction of an ADO <legacyBold>Stream</legacyBold> object (<codeInline>adoStr</codeInline>) amounts to the following three basic operations:</para>
      <list class="ordered">
        <listItem>
          <para>Create an ADO <legacyBold>Stream</legacyBold> object: </para>
          <code>Stream20Ptr adoStr;
adoStr.CreateInstance(__uuidof(Stream));</code>
        </listItem>
        <listItem>
          <para>Query the <legacyBold>IADOStreamConstruction</legacyBold> interface on the <legacyBold>Stream</legacyBold> object: </para>
          <code>adoStreamConstructionPtr adoStrConstruct=NULL;
adoStr-&gt;QueryInterface(__uuidof(ADOStreamConstruction),
                     (void**)&amp;adoStrConstruct);</code>
        </listItem>
      </list>
      <para>Call the <codeInline>IADOStreamConstruction::get_Stream</codeInline> property method to set the OLE DB <legacyBold>IStream</legacyBold> object on the ADO <legacyBold>Stream</legacyBold> object: </para>
      <code>IUnknown *pUnk=NULL;
pRowset-&gt;QueryInterface(IID_IUnknown, (void**)&amp;pUnk);
adoStrConstruct-&gt;put_Stream(pUnk);</code>
      <para>The resultant <codeInline>adoStr</codeInline> object now represents the ADO <legacyBold>Stream</legacyBold> object constructed from the OLE DB <legacyBold>IStream</legacyBold> object.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Requirements</title>
    <content>
      <para>
        <legacyBold>Version:</legacyBold> ADO 2.0 or a later version</para>
      <para>
        <legacyBold>Library:</legacyBold> msado15.dll</para>
      <para>
        <legacyBold>UUID:</legacyBold> 00000283-0000-0010-8000-00AA006D2EA4</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="bfd96a4b-c913-45aa-9e4c-ec86ac364f3a">ADO API Reference</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>