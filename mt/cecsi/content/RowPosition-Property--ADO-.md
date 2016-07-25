---
title: "RowPosition Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
caps.latest.revision: 10
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
# RowPosition Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Gets or sets an OLE DB <legacyBold>RowPosition</legacyBold> object from/on an <legacyBold>ADORecordsetConstruction</legacyBold> object. When you use <legacyBold>put_RowPosition</legacyBold> to set the <legacyBold>RowPosition</legacyBold> object, the resulting <legacyBold>Recordset</legacyBold> object uses the <legacyBold>RowPosition</legacyBold> object to determine the current row. </para>
    <para>Read/write.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);
HRESULT put_RowPosition([in] IUnknown* pRowPos);</code>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ppRowPos</legacyItalic> </definedTerm>
        <definition>
          <para>Pointer to an OLE DB <legacyBold>RowPosition</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>PRowPos</legacyItalic> </definedTerm>
        <definition>
          <para>An OLE DB <legacyBold>RowPosition</legacyBold> object.</para>
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
  <languageReferenceRemarks>
    <content>
      <para>When this property is set, if the <legacyBold>Rowset</legacyBold> object on the <legacyBold>RowPosition</legacyBold> object is different from the <legacyBold>Rowset</legacyBold> object on the <legacyBold>Recordset</legacyBold> object, the former overrides the latter. The same behavior applies to the current <legacyBold>Chapter</legacyBold> of the <legacyBold>RowPosition</legacyBold> as well.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="08386eba-f1f7-4879-8ffd-8733930ecb2f">ADORecordsetConstruction</link>       </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>