---
title: "get_OLEDBCommand Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: 4
manager: sonalm
---
# get_OLEDBCommand Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns the underlying OLE DB Command, first propagating any parameter information set on the ADO Command to the OLE DB Command.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
HRESULT get_OLEDBCommand(
      IUnknown **<parameterReference>ppOLEDBCommand</parameterReference>
);</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>ppOLEDBCommand</parameterReference>
        </definedTerm>
        <definition>
          <para>[out] A pointer to a pointer location where the IUnknown pointer for the underlying OLE DB Command will be written.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <legacyLink xlink:href="d8e54333-00eb-4b72-bf4a-ca92c7ca5f86">IADOCommandConstruction</legacyLink>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>