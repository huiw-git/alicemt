---
title: "Using ADO with ADO MD"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
caps.latest.revision: 11
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
# Using ADO with ADO MD
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO and ADO MD are related but separate object models. ADO provides objects for connecting to data sources, executing commands, retrieving tabular data and schema metadata in a tabular format, and viewing provider error information. ADO MD provides objects for retrieving multidimensional data and viewing multidimensional schema metadata.</para>
    <para>When you work with an MDP, you can choose to use ADO, ADO MD, or both with your application. By referencing both libraries within your project, you will have full access to the functionality provided by your MDP.</para>
    <para>It is frequently useful for consumers to get a flattened, tabular view of a multidimensional dataset. You can do this by using the ADO <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object. Specify the source for your <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> as the <legacyBold><legacyItalic>Source</legacyItalic></legacyBold> parameter for the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method of a <legacyBold>Recordset</legacyBold>, rather than as the source for an ADO MD <legacyBold>Cellset</legacyBold>.</para>
    <para>It may also be useful to view the schema metadata in a tabular view rather than as a hierarchy of objects. The ADO <legacyLink xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema</legacyLink> method on the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object lets the user open a <legacyBold>Recordset</legacyBold> that contains schema information. The <legacyBold><legacyItalic>QueryType</legacyItalic></legacyBold> parameter of the <legacyBold>OpenSchema</legacyBold> method has several <legacyLink xlink:href="21c97651-297f-469f-b5b5-c48af72b62a8">SchemaEnum</legacyLink> values that relate specifically to MDPs. These values are as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>adSchemaCubes</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>adSchemaDimensions</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>adSchemaHierarchies</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>adSchemaLevels</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>adSchemaMeasures</legacyBold>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>adSchemaMembers</legacyBold>           </para>
      </listItem>
    </list>
    <para>To use ADO enumeration values with ADO MD properties or methods, your project must reference both the ADO and ADO MD libraries. For example, you can use the ADO <legacyBold>adState</legacyBold> enumeration values with the ADO MD <legacyLink xlink:href="06d480ca-9eb6-4570-a45d-a73539bddd32">State</legacyLink> property. For more information about how to establish references to libraries, see the documentation of your development tool.</para>
    <para>For more information about the ADO objects and methods, see the <legacyLink xlink:href="bfd96a4b-c913-45aa-9e4c-ec86ac364f3a">ADO API Reference</legacyLink>.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="6242b374-091b-406f-827a-c0dcd3e1967a">ADO MD Object Model</link>
<link xlink:href="75b774a5-fa94-490a-b521-b2b8f7d48919">Microsoft ADO MD Programmer's Reference</link>
<link xlink:href="ce37fa06-c581-4d80-9a9b-c3aa66408909">Overview of Multidimensional Schemas and Data</link>
<link xlink:href="c826b9b5-0d78-43a2-8174-5844db62a93c">Programming with ADO MD</link>
<link xlink:href="84387746-aa3e-44fd-ad6c-a8214a6966dc">Working with Multidimensional Data</link>
</relatedTopics>
</developerConceptualDocument>