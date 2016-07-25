---
title: "Rowset Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 7d359294-4ff2-47e0-8111-0c221b24d80e
caps.latest.revision: 9
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
# Rowset Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Gets or sets an OLE DB <legacyBold>Rowset</legacyBold> object from/on an <legacyBold>ADORecordsetConstruction</legacyBold> object. When you use put_Rowset, the rowset is turned into an ADO <legacyBold>Recordset</legacyBold> object.</para>
    <para>Read/write.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>HRESULT get_Rowset([out, retval] IUnknown** ppRowset);
HRESULT put_Rowset([in] IUnknown* pRowset);</code>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ppRowset</legacyItalic> </definedTerm>
        <definition>
          <para>Pointer to an OLE DB <legacyBold>Rowset</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>PRowset</legacyItalic> </definedTerm>
        <definition>
          <para>An OLE DB <legacyBold>Rowset</legacyBold> object.</para>
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
        <link xlink:href="08386eba-f1f7-4879-8ffd-8733930ecb2f">ADORecordsetConstruction</link>       </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>