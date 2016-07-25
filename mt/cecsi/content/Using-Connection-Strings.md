---
title: "Using Connection Strings"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using Connection Strings
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can use a connection string to connect to a Visual FoxPro data source.</para>
  </introduction>
  <section>
    <content>
      <para>For example, to connect to the TasTrade data source and override the current setting of Exclusive associated with the data source, you would use the string:</para>
      <code>   DSN=TasTrade;Exclusive=Yes</code>
      <para>For a list of the attribute keywords and values you can include in the connection string, see <legacyLink xlink:href="10492c8f-3a18-4971-9db8-879e878083b9">SQLDriverConnect</legacyLink>.</para>
      <para>For a complete explanation of connection string syntax, see <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>