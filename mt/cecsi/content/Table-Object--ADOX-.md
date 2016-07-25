---
title: "Table Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
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
# Table Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a database table including columns, indexes, and keys.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The following code creates a new <legacyBold>Table</legacyBold>:</para>
      <code>Dim obj As New Table</code>
      <para>With the properties and collections of a <legacyBold>Table</legacyBold> object, you can:</para>
      <list class="bullet">
        <listItem>
          <para>Identify the table with the <link xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name Property (ADOX)</link> property.</para>
        </listItem>
        <listItem>
          <para>Determine the type of table with the <link xlink:href="7b6e14bb-fb69-4d74-aaca-f5d380f4d887">Type Property (Table) (ADOX)</link> property.</para>
        </listItem>
        <listItem>
          <para>Access the database columns of the table with the <link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection (ADOX)</link> collection.</para>
        </listItem>
        <listItem>
          <para>Access the indexes of the table with the <link xlink:href="184cf536-455c-42be-bf1c-a5c25bade961">Indexes Collection (ADOX)</link>.</para>
        </listItem>
        <listItem>
          <para>Access the keys of the table with the <link xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys Collection (ADOX)</link>.</para>
        </listItem>
        <listItem>
          <para>Specify the Catalog that owns the table with the <link xlink:href="a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273">ParentCatalog Property (ADOX)</link> property.</para>
        </listItem>
        <listItem>
          <para>Return date information with the <link xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated Property (ADOX)</link> and <link xlink:href="fed09266-1547-4bda-9088-c254d81cc738">DateModified Property (ADOX)</link> properties.</para>
        </listItem>
        <listItem>
          <para>Access provider-specific table properties with the <link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection (ADO)</link> collection.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>Your data provider may not support all properties of <legacyBold>Table</legacyBold> objects. An error will occur if you have set a value for a property that the provider does not support. For new <legacyBold>Table</legacyBold> objects, the error will occur when the object is appended to the collection. For existing objects, the error will occur when setting the property.</para>
        <para>When creating <legacyBold>Table</legacyBold> objects, the existence of an appropriate default value for an optional property does not guarantee that your provider supports the property. For more information about which properties your provider supports, see your provider documentation.</para>
      </alert>
      <para>This section contains the following topic.</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="140d1517-6f0c-4fc9-9deb-9658982d88ed">Table Object Properties, Methods, and Events</link>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="bb3274b1-764d-43a7-a49f-ef55680ecd26">Catalog ActiveConnection Property Example (VB)</link>
<link xlink:href="678e5546-df5d-4cd0-bfe9-6cf13cb385c0">Columns and Tables Append Methods, Name Property Example (VB)</link>
<link xlink:href="f88e7a3b-19ed-46e2-b2ce-3b611d9b8166">Connection Close Method, Table Type Property Example (VB)</link>
<link xlink:href="13b5b1c3-6af6-439e-bb65-976578ba6bc2">Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)</link>
<link xlink:href="448bc850-7584-4c5f-89f3-5f4fee88b259">ParentCatalog Property Example (VB)</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection (ADOX)</link>
<link xlink:href="184cf536-455c-42be-bf1c-a5c25bade961">Indexes Collection (ADOX)</link>
<link xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys Collection (ADOX)</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection (ADO)</link>
<link xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection (ADOX)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>