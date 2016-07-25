---
title: "OpenSchema Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
caps.latest.revision: 20
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
# OpenSchema Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Obtains database schema information from the provider.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set </legacyBold><parameterReference>recordset</parameterReference> = <parameterReference>connection</parameterReference><legacyBold>.OpenSchema(</legacyBold><parameterReference>QueryType</parameterReference>, <parameterReference>Criteria</parameterReference>, <parameterReference>SchemaID</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object that contains schema information. The <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> will be opened as a read-only, static cursor. The <legacyItalic>QueryType</legacyItalic> determines what columns appear in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>QueryType </parameterReference></definedTerm>
        <definition>
          <para>Any <legacyLink xlink:href="21c97651-297f-469f-b5b5-c48af72b62a8">SchemaEnum</legacyLink> value that represents the type of schema query to run.</para>
        </definition>
        <definedTerm> <parameterReference>Criteria </parameterReference></definedTerm>
        <definition>
          <para>Optional. An array of query constraints for each <parameterReference>QueryType</parameterReference> option, as listed in <legacyLink xlink:href="21c97651-297f-469f-b5b5-c48af72b62a8">SchemaEnum</legacyLink>.</para>
        </definition>
        <definedTerm> <parameterReference>SchemaID </parameterReference></definedTerm>
        <definition>
          <para>The GUID for a provider-schema query not defined by the OLE DB specification. This parameter is required if <parameterReference>QueryType</parameterReference> is set to <legacyBold>adSchemaProviderSpecific</legacyBold>; otherwise, it is not used.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <unmanagedCodeEntityReference>OpenSchema</unmanagedCodeEntityReference> method returns self-descriptive information about the data source, such as what tables are in the data source, the columns in the tables, and the data types supported.</para>
      <para>The <parameterReference>QueryType</parameterReference> argument is a GUID that indicates the columns (schemas) returned. The OLE DB specification has a full list of schemas.</para>
      <para>The <parameterReference>Criteria</parameterReference> argument limits the results of a schema query. <parameterReference>Criteria</parameterReference> specifies an array of values that must occur in a corresponding subset of columns, called constraint columns, in the resulting <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
      <para>The constant <legacyBold>adSchemaProviderSpecific</legacyBold> is used for the <parameterReference>QueryType</parameterReference> argument if the provider defines its own nonstandard schema queries outside those listed previously. When this constant is used, the <parameterReference>SchemaID</parameterReference> argument is required to pass the GUID of the schema query to execute. If <parameterReference>QueryType</parameterReference> is set to <legacyBold>adSchemaProviderSpecific</legacyBold> but <parameterReference>SchemaID</parameterReference> is not provided, an error will result.</para>
      <para>Providers are not required to support all the OLE DB standard schema queries. Specifically, only <legacyBold>adSchemaTables</legacyBold>, <legacyBold>adSchemaColumns</legacyBold>, and <legacyBold>adSchemaProviderTypes</legacyBold> are required by the OLE DB specification. However, the provider is not required to support the <parameterReference>Criteria</parameterReference> constraints listed earlier for those schema queries.</para>
      <alert class="note">
        <para>
          <legacyBold>Remote Data Service Usage</legacyBold>   The <unmanagedCodeEntityReference>OpenSchema</unmanagedCodeEntityReference> method is not available on a client-side <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
      </alert>
      <alert class="note">
        <para>In Visual Basic, columns that have a four-byte unsigned integer (DBTYPE UI4) in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> returned from the <unmanagedCodeEntityReference>OpenSchema</unmanagedCodeEntityReference> method on the <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object cannot be compared to other variables. For more information about OLE DB data types, see <legacyLink xlink:href="6039292f-74e0-49b2-b133-17bc117ebf6a">Data Types in OLE DB (OLE DB)</legacyLink> and <legacyLink xlink:href="e3a0533a-2196-4eb0-a31e-92fe9556ada6">Appendix A: Data Types</legacyLink> in the Microsoft OLE DB Programmer's Reference.</para>
      </alert>
      <alert class="note">
        <para>
          <legacyBold>Visual C/C++ Users</legacyBold>   When not using client-side cursors, retrieving the "ORDINAL_POSITION" of a column schema in ADO returns a variant of type VT_R8 in MDAC 2.7, MDAC 2.8, and Windows Data Access Components (Windows DAC) 6.0, while the type used in MDAC 2.6 was VT_I4. Programs written for MDAC 2.6 that only look for a variant returned of type VT_I4 would get a zero for every ordinal if run under MDAC 2.7, MDAC 2.8, and Windows DAC 6.0 without modification. This change was made because the data type that OLE DB returns is DBTYPE_UI4, and in the signed VT_I4 type there is not enough room to contain all possible values without possibly truncation occurring and thereby causing a loss of data.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="455a02f0-8143-4562-8648-8fb45ffd334c">Visual Basic Example</link>
<link xlink:href="6f3da460-0f49-41e0-999d-a754ec1d887e">Visual C++ Example</link>
<link xlink:href="4c1240f1-7464-47db-9761-2d547419aedd">Visual J++ Example</link>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>