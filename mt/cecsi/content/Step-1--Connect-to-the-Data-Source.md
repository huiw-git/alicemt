---
title: Step 1: Connect to the Data Source
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Step 1: Connect to the Data Source
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The first step in any application is to connect to the data source. This phase, including the functions it requires, is shown in the following illustration. </para>
    <mediaLink>
      <image xlink:href="db8dafd6-e37f-4adc-979a-bdcd56f14042" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>The first step in connecting to the data source is to load the Driver Manager and allocate the environment handle with <legacyBold>SQLAllocHandle</legacyBold>. For more information, see <legacyLink xlink:href="77b5d1d6-7eb7-428d-bf75-a5c5a325d25c">Allocating the Environment Handle</legacyLink>.</para>
      <para>The application then registers the version of ODBC to which it conforms by calling <legacyBold>SQLSetEnvAttr</legacyBold> with the SQL_ATTR_APP_ODBC_VER environment attribute. For more information, see <legacyLink xlink:href="083a1ef5-580a-4979-9cf3-50f4549a080a">Declaring the Application's ODBC Version</legacyLink> and <legacyLink xlink:href="b5eee7be-28ed-4467-8cf1-2205e2010a53">Backward Compatibility and Standards Compliance</legacyLink>.</para>
      <para>Next, the application allocates a connection handle with <legacyBold>SQLAllocHandle</legacyBold> and connects to the data source with <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, or <legacyBold>SQLBrowseConnect</legacyBold>. For more information, see <legacyLink xlink:href="c99a8159-7693-4f97-8dcf-401336550e77">Allocating a Connection Handle</legacyLink> and <legacyLink xlink:href="8e3c717e-35e3-47ef-b5d3-3a96eeb7b869">Establishing a Connection</legacyLink>.</para>
      <para>The application then sets any connection attributes, such as whether to manually commit transactions. For more information, see <legacyLink xlink:href="e6d03089-30a3-4627-a642-591ba0980894">Connection Attributes</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>