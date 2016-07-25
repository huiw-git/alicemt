---
title: "IDSOShapeExtensions Interface"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad4ba313-1161-4bc7-b8f6-4083305bc81e
caps.latest.revision: 3
manager: sonalm
---
# IDSOShapeExtensions Interface
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Gets the underlying OLE DB Data Source object for the SHAPE provider.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
interface IDSOShapeExtensions: public IUnknown {
public:
      HRESULT  GetDataProviderDSO(
            IUnknown **ppDataProviderDSOIUnknown
      );
};</legacySyntax>
  </syntaxSection>
  <section>
    <title>Methods</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="5a4c6bd5-0c79-4f81-a977-0561392d8d50">GetDataProviderDSO</link>
              </para>
            </TD>
            <TD>
              <para>Retrieves the underlying OLE DB Data Source object from the Shape provider.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <requirements>
    <content>
      <para>
        <legacyBold>Version:</legacyBold> ADO 2.0 and later</para>
      <para>
        <legacyBold>Library:</legacyBold> msado15.dll</para>
      <para>
        <legacyBold>UUID:</legacyBold> 00000283-0000-0010-8000-00AA006D2EA4</para>
    </content>
  </requirements>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>