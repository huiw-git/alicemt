---
title: "ADO MD Fundamentals"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
caps.latest.revision: 13
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
# ADO MD Fundamentals
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Microsoft® ActiveX® Data Objects (Multidimensional) (ADO MD) provides easy access to multidimensional data from languages such as Microsoft Visual Basic®, Microsoft Visual C++®, and Microsoft Visual J++®. ADO MD extends Microsoft ActiveX® Data Objects (ADO) to include objects specific to multidimensional data, such as the <legacyLink xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef</legacyLink> and <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> objects. With ADO MD you can browse multidimensional schema, query a cube, and retrieve the results.</para>
    <para>Like ADO, ADO MD uses an underlying OLE DB provider to gain access to data. To work with ADO MD, the provider must be a multidimensional data provider (MDP) as defined by the OLE DB for OLAP specification. An MDP presents data in multidimensional views instead of tabular views, which is how a tabular data provider (TDP) presents data. Refer to the documentation for your OLAP OLE DB provider for more information about the specific syntax and behavior supported by your provider.</para>
    <para>This document assumes a working knowledge of the Visual Basic programming language and a general knowledge of ADO and OLAP. For more information, see the <legacyLink xlink:href="e3c50eee-964a-4abd-810d-1bd51978e814">ADO Programmer's Guide</legacyLink> and <externalLink><linkText>OLE DB for Online Analytical Processing (OLAP)</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx</linkUri></externalLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="ce37fa06-c581-4d80-9a9b-c3aa66408909">Overview of Multidimensional Schemas and Data</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="84387746-aa3e-44fd-ad6c-a8214a6966dc">Working with Multidimensional Data</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="cfae435e-2ac3-4312-8c1e-9ca4a74cd875">Using ADO with ADO MD</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="c826b9b5-0d78-43a2-8174-5844db62a93c">Programming with ADO MD</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="6242b374-091b-406f-827a-c0dcd3e1967a">ADO MD Object Model</link>
<link xlink:href="e3c50eee-964a-4abd-810d-1bd51978e814">Microsoft ADO Programmer's Guide</link>
<link xlink:href="c6579b5b-a93e-48c5-8847-743fc4590cd2">Microsoft ADOX Programmer's Reference</link>
<link xlink:href="ce37fa06-c581-4d80-9a9b-c3aa66408909">Overview of Multidimensional Schemas and Data</link>
<link xlink:href="c826b9b5-0d78-43a2-8174-5844db62a93c">Programming with ADO MD</link>
<link xlink:href="cfae435e-2ac3-4312-8c1e-9ca4a74cd875">Using ADO with ADO MD</link>
<link xlink:href="84387746-aa3e-44fd-ad6c-a8214a6966dc">Working with Multidimensional Data</link>
</relatedTopics>
</developerConceptualDocument>