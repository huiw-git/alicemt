---
title: "ParentRow Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
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
# ParentRow Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Sets the container of an OLE DB <legacyBold>Row</legacyBold> object on an <legacyBold>ADORecordConstruction</legacyBold> object, so that the parent of the row is turned into an ADO <legacyBold>Record</legacyBold> object.</para>
    <para>Write-only.       </para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>HRESULT put_ParentRow([in] IUnknown* pParent);</code>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>pParent</legacyItalic> </definedTerm>
        <definition>
          <para>A container of a row.</para>
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
        <link xlink:href="52a5429e-5829-455e-be3b-31f05cbecf2d">ADORecordConstruction</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>