---
title: "Step 6: Disconnect from the Data Source"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Step 6: Disconnect from the Data Source
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The final step is to disconnect from the data source, as shown in the following illustration. First, the application frees any statement handles by calling <legacyBold>SQLFreeHandle</legacyBold>. For more information, see <legacyLink xlink:href="ee18e2f1-2690-4cc1-9e5c-e20244e5d480">Freeing a Statement Handle</legacyLink>.</para>
    <mediaLink>
      <image xlink:href="792336b3-c80d-4c45-94b9-2b74692afdec" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>Next, the application disconnects from the data source with <legacyBold>SQLDisconnect</legacyBold> and frees the connection handle with <legacyBold>SQLFreeHandle</legacyBold>. For more information, see <legacyLink xlink:href="83dbf0bf-b400-41fb-8537-9b016050dc3c">Disconnecting from a Data Source or Driver</legacyLink>.</para>
      <para>Finally, the application frees the environment handle with <legacyBold>SQLFreeHandle</legacyBold> and unloads the Driver Manager. For more information, see <legacyLink xlink:href="77b5d1d6-7eb7-428d-bf75-a5c5a325d25c">Allocating the Environment Handle</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>