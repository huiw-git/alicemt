---
title: "ADCPROP_AUTORECALC_ENUM"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
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
# ADCPROP_AUTORECALC_ENUM
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies when the <legacyLink xlink:href="523009ce-e01b-4e2d-a7df-816d7688aff0">MSDataShape</legacyLink> provider re-calculates aggregate and calculated columns in a hierarchical Recordset.</para>
    <para>These constants are only used with the <legacyBold>MSDataShape</legacyBold> provider and the <legacyBold>Recordset</legacyBold> "<legacyBold>Auto Recalc</legacyBold>" dynamic property, which is referenced in the <legacyLink xlink:href="80d389dd-46ef-459f-b0d4-6f712fc4f32d">ADO Dynamic Property Index</legacyLink> and documented in the <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Microsoft Cursor Service for OLE DB</legacyLink> or <legacyLink xlink:href="523009ce-e01b-4e2d-a7df-816d7688aff0">Microsoft Data Shaping Service for OLE DB</legacyLink> documentation.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Constant</para>
          </TD>
          <TD>
            <para>Value</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecalcAlways</legacyBold>           </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Default. Recalculates whenever the <legacyBold>MSDataShape</legacyBold> provider determines values that the calculated columns depend upon have changed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecalcUpFront</legacyBold>           </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Calculates only when initially building the hierarchical <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>These constants do not have ADO/WFC equivalents.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>