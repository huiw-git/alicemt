---
title: "Stream Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
caps.latest.revision: 5
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
# Stream Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Gets or sets an OLE DB <legacyBold>Stream</legacyBold> object from/on an <legacyBold>ADOStreamConstruction</legacyBold> object.  </para>
    <para>Read/write.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>HRESULT get_Stream([out, retval] IUnknown** ppStream);
HRESULT put_Stream([in] IUnknown* pStream);</code>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>ppStream</legacyItalic>
        </definedTerm>
        <definition>
          <para>Pointer to an OLE DB <legacyBold>Stream</legacyBold> object.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pStream</legacyItalic>
        </definedTerm>
        <definition>
          <para>An OLE DB <legacyBold>Stream</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Return Values</title>
    <content>
      <para>This property method returns the standard HRESULT values. This includes S_OK and E_FAIL.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="92f5a939-3e1a-4b14-a9dd-90e6ce2dec74">ADOStreamConstruction</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>