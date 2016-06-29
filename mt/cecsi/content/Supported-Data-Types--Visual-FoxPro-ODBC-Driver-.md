---
title: Supported Data Types (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
translation.priority.ht: 
  - en-gb
---
# Supported Data Types (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The list of data types supported by the driver are presented through the ODBC API and in Microsoft Query.</para>
  </introduction>
  <section>
    <title>Data Types in C Applications</title>
    <content>
      <para>You can obtain a list of data types supported by the Visual FoxPro ODBC Driver by using the <legacyLink xlink:href="5f25e20b-a4ef-42da-aeb6-00e0510fb1cc">SQLGetTypeInfo</legacyLink> function in C or C++ applications.</para>
    </content>
  </section>
  <section>
    <title>Data Types in Applications Using Microsoft Query</title>
    <content>
      <para>If your application uses Microsoft Query to create a new table on a Visual FoxPro data source, Microsoft Query displays the <legacyBold>New Table Definition</legacyBold> dialog box. Under <legacyBold>Field Description</legacyBold>, the <legacyBold>Type</legacyBold> box lists <legacyLink xlink:href="50b733dc-679a-4b10-bc5d-98bb474dead2">Visual FoxPro field data types</legacyLink>, represented by single characters.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>