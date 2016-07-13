---
title: Step 2: Initialize the Application
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Step 2: Initialize the Application
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The second step is to initialize the application, as shown in the following illustration. Exactly what is done here varies with the application.</para>
    <mediaLink>
      <image xlink:href="39974243-cfef-498b-9cf1-8d0f772195eb" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>At this point, it is common to use <legacyBold>SQLGetInfo</legacyBold> to discover the capabilities of the driver. For more information, see <legacyLink xlink:href="59760114-508e-46c5-81d2-8f2498c0d778">Considering Database Features to Use</legacyLink>.</para>
      <para>All applications need to allocate a statement handle with <legacyBold>SQLAllocHandle</legacyBold>, and many applications set statement attributes, such as the cursor type, with <legacyBold>SQLSetStmtAttr</legacyBold>. For more information, see <legacyLink xlink:href="4ce3b446-34ab-46dc-96e5-f40ec95c267e">Allocating a Statement Handle</legacyLink> and <legacyLink xlink:href="4c59cd8e-a713-4095-9065-20d5bdeafe43">Statement Attributes</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>