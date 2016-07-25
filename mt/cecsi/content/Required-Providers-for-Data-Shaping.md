---
title: "Required Providers for Data Shaping"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
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
# Required Providers for Data Shaping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data shaping typically requires two providers. The service provider, <legacyLink xlink:href="523009ce-e01b-4e2d-a7df-816d7688aff0">Data Shaping Service for OLE DB</legacyLink>, supplies the data shaping functionality, and a data provider, such as the OLE DB Provider for SQL Server, supplies rows of data to populate the shaped <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <para>The name of the service provider (MSDataShape) can be specified as the value of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property or the connection string keyword "Provider=MSDataShape;".</para>
    <para>The name of the data provider can be specified as the value of the <legacyBold>Data Provider</legacyBold> dynamic property, which is added to the <legacyBold>Connection</legacyBold> object <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection by the Data Shaping Service for OLE DB, or the connection string keyword "<legacyBold>Data Provider=</legacyBold><legacyItalic>provider</legacyItalic>".</para>
    <para>No data provider is required if the <legacyBold>Recordset</legacyBold> is not populated (for example, as in a fabricated <legacyBold>Recordset</legacyBold> where columns are created with the NEW keyword). In that case, specify "<legacyBold>Data Provider=</legacyBold>none;".</para>
  </introduction>
  <codeExample>
    <code>Dim cnn As New ADODB.Connection
cnn.Provider = "MSDataShape"
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"</code>
  </codeExample>
  <relatedTopics>
<link xlink:href="1bfdcad4-52e1-45bc-ad21-783657ef0a44">Data Shaping</link>
<link xlink:href="ea691475-0f03-4abe-a785-b77e77712d1d">Formal Shape Grammar</link>
<link xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>