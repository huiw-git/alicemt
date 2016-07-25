---
title: "Provider Support for ADOX (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
caps.latest.revision: 5
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
# Provider Support for ADOX (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Certain features of ADOX are unsupported, depending on your OLE DB data provider. ADOX is fully supported with the <legacyLink xlink:href="fd956da1-5203-40af-aa7e-fc13a6c6581f">OLE DB Provider for Microsoft Jet</legacyLink>. The unsupported features with the <legacyLink xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">Microsoft OLE DB Provider for SQL Server</legacyLink>, the <legacyLink xlink:href="2dc0372d-e74d-4d0f-9c8c-04e5a168c148">Microsoft OLE DB Provider for ODBC</legacyLink>, or the <legacyLink xlink:href="44fae9dd-5585-4cd6-8bbd-3248a78931b4">Microsoft OLE DB Provider for Oracle</legacyLink> are listed in the following tables. ADOX is not supported by any other Microsoft OLE DB providers.</para>
  </introduction>
  <section>
    <title>Microsoft OLE DB Provider for SQL Server</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Object or Collection</para>
            </TD>
            <TD>
              <para>Usage Restriction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>Tables</legacyBold> collection</para>
            </TD>
            <TD>
              <para>Properties are read/write prior to object creation, and read-only when referencing an existing object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Views</legacyBold> collection</para>
            </TD>
            <TD>
              <para>               <legacyBold>Views</legacyBold> is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Procedures</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Procedure</legacyBold> object</para>
            </TD>
            <TD>
              <para>The <legacyBold>Command</legacyBold> property is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Keys</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Users</legacyBold> collection</para>
            </TD>
            <TD>
              <para>               <legacyBold>Users</legacyBold> is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Groups</legacyBold> collection</para>
            </TD>
            <TD>
              <para>               <legacyBold>Groups</legacyBold> is not supported.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Microsoft OLE DB Provider for ODBC</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Object or Collection</para>
            </TD>
            <TD>
              <para>Usage Restriction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>Catalog</legacyBold> object</para>
            </TD>
            <TD>
              <para>The <legacyBold>Create</legacyBold> method is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Tables</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported. Properties are read/write prior to object creation, and read-only when referencing an existing object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Procedures</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Procedure</legacyBold> object</para>
            </TD>
            <TD>
              <para>The <legacyBold>Command</legacyBold> property is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Indexes</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Keys</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Users</legacyBold> collection</para>
            </TD>
            <TD>
              <para>               <legacyBold>Users</legacyBold> is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Groups</legacyBold> collection</para>
            </TD>
            <TD>
              <para>               <legacyBold>Groups</legacyBold> is not supported.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Microsoft OLE DB Provider for Oracle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Object or Collection</para>
            </TD>
            <TD>
              <para>Usage Restriction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>Catalog</legacyBold> object</para>
            </TD>
            <TD>
              <para>The <legacyBold>Create</legacyBold> method is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Tables</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported. Properties are read/write prior to object creation, and read-only when referencing an existing object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Views</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>View</legacyBold> object</para>
            </TD>
            <TD>
              <para>The <legacyBold>Command</legacyBold> property is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Procedures</legacyBold> object</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Procedure</legacyBold> object</para>
            </TD>
            <TD>
              <para>The <legacyBold>Command</legacyBold> property is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Indexes</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Keys</legacyBold> collection</para>
            </TD>
            <TD>
              <para>The <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods are not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Users</legacyBold> collection</para>
            </TD>
            <TD>
              <para>               <legacyBold>Users</legacyBold> is not supported.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Groups</legacyBold> collection</para>
            </TD>
            <TD>
              <para>               <legacyBold>Groups</legacyBold> is not supported.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>