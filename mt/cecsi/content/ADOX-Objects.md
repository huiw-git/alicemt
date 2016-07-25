---
title: "ADOX Objects"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f5287e9-f62c-40c4-bb59-985102be956e
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
# ADOX Objects
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>ADOX Object Summary</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Object</para>
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
                <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink>             </para>
            </TD>
            <TD>
              <para>Contains collections that describe the schema catalog of a data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents a column from a table, index, or key.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents a group account that has access permissions within a secured database.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents an index from a database table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents a primary, foreign, or unique key field from a database table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="927bcf3e-32f5-4a80-98d3-600779f0732e">Procedure</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents a stored procedure.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents a database table, including columns, indexes, and keys.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents a user account that has access permissions within a secured database.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="653421ce-7b94-43d0-9bc6-4900f8f2af45">View</legacyLink>             </para>
            </TD>
            <TD>
              <para>Represents a filtered set of records or a virtual table.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The relationships between these objects are illustrated in the <legacyLink xlink:href="31c0781c-96c8-4460-90ea-134066154fc7">ADOX Object Model</legacyLink>.</para>
      <para>Each object can be contained in its corresponding collection. For example, a <legacyBold>Table</legacyBold> object can be contained in a <legacyLink xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables</legacyLink> collection. For more information, see <legacyLink xlink:href="c0c90ba9-0471-4381-96f1-376de22fa2ee">ADOX Collections</legacyLink> or a specific collection topic.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ef700465-2e97-46e8-8213-2d662501e540">ADOX API Reference</link>
<link xlink:href="c0c90ba9-0471-4381-96f1-376de22fa2ee">ADOX Collections</link>
<link xlink:href="31c0781c-96c8-4460-90ea-134066154fc7">ADOX Object Model</link>
<link xlink:href="c6579b5b-a93e-48c5-8847-743fc4590cd2">Microsoft ADOX Programmer's Reference</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>