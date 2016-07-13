---
title: Basic ODBC Application Steps
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a92d1f78-c669-47ad-88c4-0b1a93503dfc
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Basic ODBC Application Steps
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This section describes the general flow of ODBC applications. It is unlikely that any application calls all of these functions in exactly this order. However, most applications use some variation of these steps. The basic application steps are shown in the following illustration.</para>
    <mediaLink>
      <image xlink:href="da14ed04-c9d9-4d8f-9b0e-25e0eb99fd3f" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="84298664-4523-4149-b821-7b2e42c85281">Step 1: Connect to the Data Source</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="23a7a230-ae2c-4a5e-9760-d2e17f92c389">Step 2: Initialize the Application</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="133b8bd4-a3c8-4f7e-93c5-c05283c8e96f">Step 3: Build and Execute an SQL Statement</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="77d30142-c774-473c-96fb-b364bb92ac60">Step 4a: Fetch the Results</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="3af481b1-d694-446e-948d-e3a5edcad050">Step 4b: Fetch the Row Count</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="311685e2-f7b5-4ddc-8020-59380cd2f035">Step 5: Commit the Transaction</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6ad759ba-4721-4d8f-9b26-de976d4fc1a0">Step 6: Disconnect from the Data Source</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>