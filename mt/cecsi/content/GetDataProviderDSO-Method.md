---
title: "GetDataProviderDSO Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: 5
manager: sonalm
---
# GetDataProviderDSO Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Retrieves the underlying OLE DB Data Source object from the Shape provider. </para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
HRESULT GetDataProviderDSO(
      IUnknown **<parameterReference>ppDataProviderDSOIUnknown</parameterReference>
);</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>ppDataProviderDSOIUnknown</parameterReference>
        </definedTerm>
        <definition>
          <para>[out]  A pointer to a pointer that returns the IUnknown of the underlying OLE DB Data Source object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>This method does not addref the interface pointer. If the caller plans to hold the pointer, the caller must do the required addref and release.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies to</title>
    <content>
      <para>
        <link xlink:href="ad4ba313-1161-4bc7-b8f6-4083305bc81e">IDSOShapeExtensions Interface</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>