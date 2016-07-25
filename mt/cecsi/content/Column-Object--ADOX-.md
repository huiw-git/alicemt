---
title: "Column Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
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
# Column Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a column from a table, index, or key.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The following code creates a new <legacyBold>Column</legacyBold>:</para>
      <para>
        <codeInline>Dim obj As New Column</codeInline>
      </para>
      <para>With the properties and collections of a <legacyBold>Column</legacyBold> object, you can:</para>
      <list class="bullet">
        <listItem>
          <para>Identify the column with the <link xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>Specify the data type of the column with the <link xlink:href="8ca2f1fd-eb1e-490c-a28b-67eda92e0fc7">Type Property (Key) (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>Determine if the column is fixed-length, or if it can contain null values with the <link xlink:href="e3abb359-79a3-4c22-b3a8-2900817e0d23">Attributes Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>Specify the maximum size of the column with the <link xlink:href="762b8937-c31c-4e90-bb85-506d991e8280">DefinedSize Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>For numeric data values, specify the scale with the <link xlink:href="573ee5d1-57c7-4a27-be79-a0e12944ad9b">NumericScale Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>For numeric data value, specify the maximum precision with the <link xlink:href="0e0ecbbf-d7de-49d4-a128-5a519ecd54ba">Precision Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>Specify the <link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object (ADOX)</link> that owns the column with the <link xlink:href="a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273">ParentCatalog Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>For key columns, specify the name of the related column in the related table with the <link xlink:href="2f2ca019-c785-4c08-beb1-3a2d3b47823e">RelatedColumn Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>For index columns, specify whether the sort order is ascending or descending with the <link xlink:href="04510b19-9cb2-4895-b23b-f7790123eb04">SortOrder Property (ADOX)</link> property. </para>
        </listItem>
        <listItem>
          <para>Access provider-specific properties with the <link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection (ADO)</link> collection. </para>
        </listItem>
      </list>
      <alert class="note">
        <para>Not all properties of <legacyBold>Column</legacyBold> objects may be supported by your data provider. An error will occur if you have set a value for a property that the provider does not support. For new <legacyBold>Column</legacyBold> objects, the error will occur when the object is appended to the collection. For existing objects, the error will occur when setting the property.</para>
        <para>When creating <legacyBold>Column</legacyBold> objects, the existence of an appropriate default value for an optional property does not guarantee that your provider supports the property. For more information about which properties your provider supports, see your provider documentation.</para>
      </alert>
      <para>This section contains the following topic.</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="f87d46fb-4b33-42b5-8a54-6d2c4577c69a">Column Object Properties, Methods, and Events</link>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="678e5546-df5d-4cd0-bfe9-6cf13cb385c0">Columns and Tables Append Methods, Name Property Example (VB)</link>
<link xlink:href="f88e7a3b-19ed-46e2-b2ce-3b611d9b8166">Connection Close Method, Table Type Property Example (VB)</link>
<link xlink:href="13b5b1c3-6af6-439e-bb65-976578ba6bc2">Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)</link>
<link xlink:href="ea2ec614-34c8-41b7-8ebd-063798bd56b4">ADOX Code Example: NumericScale and Precision Properties Example (VB)</link>
<link xlink:href="448bc850-7584-4c5f-89f3-5f4fee88b259">ParentCatalog Property Example (VB)</link>
<link xlink:href="d9502254-d89b-4bcb-94f1-6418f89e7f30">SortOrder Property Example (VB)</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection (ADOX)</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection (ADO)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>