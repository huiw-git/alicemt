---
title: "Row Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
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
# Row Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Gets or sets an OLE DB <legacyBold>Row</legacyBold> object from or on an <link xlink:href="52a5429e-5829-455e-be3b-31f05cbecf2d">ADORecordConstruction Interface</link> object. When you use <legacyBold>put_Row</legacyBold> to set a <legacyBold>Row</legacyBold> object, a row is turned into an ADO <legacyBold>Record</legacyBold> object.</para>
  </introduction>
  <section>
    <title>Read/write.Syntax</title>
    <content>
      <code>HRESULT get_Row([out, retval] IUnknown** ppRow);
HRESULT put_Row([in] IUnknown* pRow);</code>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ppRow</legacyItalic> </definedTerm>
        <definition>
          <para>Pointer to an OLE DB <legacyBold>Row</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>PRow</legacyItalic> </definedTerm>
        <definition>
          <para>An OLE DB <legacyBold>Row</legacyBold> object.</para>
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
        <link xlink:href="52a5429e-5829-455e-be3b-31f05cbecf2d">ADORecordConstruction Interface</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>