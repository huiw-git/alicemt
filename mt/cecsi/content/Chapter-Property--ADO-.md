---
title: "Chapter Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
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
# Chapter Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Gets or sets an OLE DB <legacyBold>Chapter</legacyBold> object from/on an <link xlink:href="08386eba-f1f7-4879-8ffd-8733930ecb2f">ADORecordsetConstruction Interface</link> object. When you use <legacyBold>put_Chapter</legacyBold> to set the <unmanagedCodeEntityReference>Chapter</unmanagedCodeEntityReference> object, a subset of rows is turned into an ADO <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</legacyLink> object. This sets the current chapter of the <legacyBold>Rowset</legacyBold><codeInline> </codeInline>object. This property is read/write.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>HRESULT get_Chapter([out, retval] long* plChapter);
HRESULT put_Chapter([in] long lChapter);</code>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>plChapter </parameterReference></definedTerm>
        <definition>
          <para>Pointer to the handle of a chapter.</para>
        </definition>
        <definedTerm> <parameterReference>LChapter </parameterReference></definedTerm>
        <definition>
          <para>Handle of a chapter.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Return Values</title>
    <content>
      <para>This property method returns the standard HRESULT values, including S_OK and E_FAIL.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="08386eba-f1f7-4879-8ffd-8733930ecb2f">ADORecordsetConstruction</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>