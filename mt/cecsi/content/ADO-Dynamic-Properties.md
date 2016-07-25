---
title: "ADO Dynamic Properties"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
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
# ADO Dynamic Properties
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Dynamic properties can be added to the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collections of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink>, or <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects. The source for these properties is either a data provider, such as the <legacyLink xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">OLE DB Provider for SQL Server</legacyLink>, or a service provider, such as the <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Microsoft Cursor Service for OLE DB</legacyLink>. Refer to the appropriate data provider or service provider documentation for more information about a specific dynamic property.</para>
    <para>The <legacyLink xlink:href="80d389dd-46ef-459f-b0d4-6f712fc4f32d">ADO Dynamic Property Index</legacyLink> provides a cross-reference between the ADO and OLE DB names for each standard OLE DB provider dynamic property.</para>
    <para>The following dynamic properties are especially interesting, and are also documented in the sources that were mentioned earlier. Special functionality with ADO is documented in the ADO help topics in the following list.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether an index should be created on this field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="c4f001b5-8d16-4d39-a42e-c0e2faaaceaf">Prompt</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether the OLE DB provider should prompt the user for initialization information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="690229d1-46cc-42e6-a57d-4438251fe248">Reshape Name</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies a name for the <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="4e2bb601-0fe8-4d61-b00e-38341d85a6bb">Resync Command</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies a user-supplied command string that the <legacyBold>Resync</legacyBold> method issues to refresh the data in the table named in the <legacyBold>Unique Table</legacyBold> dynamic property.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table, Unique Schema, Unique Catalog</legacyLink>             </para>
          </TD>
          <TD>
            <para>
              <legacyBold>Unique Table</legacyBold>     Specifies the name of the base table upon which updates, insertions, and deletions are allowed.</para>
            <para>
              <legacyBold>Unique Schema</legacyBold>     Specifies the schema, or name of the owner of the table.</para>
            <para>
              <legacyBold>Unique Catalog</legacyBold>     Specifies the catalog, or name of the database that contains the table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="8a3bb608-66d7-4128-a3ef-84cb0556de0d">Update Resync</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether the <legacyBold>UpdateBatch</legacyBold> method is followed by an implicit <legacyBold>Resync</legacyBold> method operation, and if so, the scope of that operation.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="bfd96a4b-c913-45aa-9e4c-ec86ac364f3a">ADO API Reference</link>
<link xlink:href="b5e1d26d-b41d-4e35-8c7c-972426473dfb">ADO Collections</link>
<link xlink:href="c97ed131-1a93-463c-9e61-22f029b0c474">ADO Enumerated Constants</link>
<link xlink:href="0ce201c3-6657-4c87-ae81-0d7dc5b5a431">ADO Errors</link>
<link xlink:href="0ded5ad9-8f83-4224-95af-38512783b972">ADO Events</link>
<link xlink:href="a38c5670-ba28-44f3-bd5b-fcb46880e904">ADO Methods</link>
<link xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</link>
<link xlink:href="d0b7e254-c89f-4406-b846-a060ef038c30">ADO Objects</link>
<link xlink:href="0ac0d1a7-6c7a-4f4c-b115-428935e0f98b">ADO Properties</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>