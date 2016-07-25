---
title: "FilterAxis Property (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
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
# FilterAxis Property (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates filter information about the current <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">cellset</legacyLink>.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns an <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink> object, and is read-only.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>FilterAxis</unmanagedCodeEntityReference> property to return information about the dimensions that were used to slice the data. The <legacyLink xlink:href="87929cbc-9c38-491a-8616-62d45c51e299">DimensionCount</legacyLink> property of the <unmanagedCodeEntityReference>Axis</unmanagedCodeEntityReference> returns the number of slicer dimensions. This axis usually has just one row.</para>
      <para>The <unmanagedCodeEntityReference>Axis</unmanagedCodeEntityReference> returned by <unmanagedCodeEntityReference>FilterAxis</unmanagedCodeEntityReference> is not contained in the <legacyLink xlink:href="072fb21a-ec0f-4b02-9022-1cef3ad4bfff">Axes</legacyLink> collection for a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object (ADO MD)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis Object</link>
<link xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">Dimension Object</link>
<link xlink:href="87929cbc-9c38-491a-8616-62d45c51e299">DimensionCount Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>