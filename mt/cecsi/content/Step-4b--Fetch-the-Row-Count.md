---
title: "Step 4b: Fetch the Row Count"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Step 4b: Fetch the Row Count
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The next step is to fetch the row count, as shown in the following illustration.</para>
    <mediaLink>
      <image xlink:href="8a5610e3-3231-4380-a709-0165aa1b34bb" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>If the statement executed in Step 3 was an <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, or <legacyBold>INSERT</legacyBold> statement, the application retrieves the count of affected rows with <legacyBold>SQLRowCount</legacyBold>. For more information, see <legacyLink xlink:href="1e56297d-a786-415e-b66d-b42d1b2a8d45">Determining the Number of Affected Rows</legacyLink>.</para>
      <para>The application now returns to step 3 to execute another statement in the same transaction or proceeds to step 5 to commit or roll back the transaction.</para>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>