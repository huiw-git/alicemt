---
title: "Updating Data"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
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
# Updating Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Update behavior and functionality is largely dependent upon update mode (lock type), cursor type, and cursor location.</para>
    <para>Use the <legacyBold>Update</legacyBold> method to save any changes you have made to the current record of a <legacyBold>Recordset</legacyBold> object since calling the <legacyBold>AddNew</legacyBold> method or since changing any field values in an existing record. The <legacyBold>Recordset</legacyBold> object must support updates.</para>
    <para>If the <legacyBold>Recordset</legacyBold> object supports batch updating, you can cache multiple changes to one or more records locally until you call the <legacyBold>UpdateBatch</legacyBold> method. If you are editing the current record or adding a new record when you call the <legacyBold>UpdateBatch</legacyBold> method, ADO will automatically call the <legacyBold>Update</legacyBold> method to save any pending changes to the current record before transmitting the batched changes to the provider.</para>
    <para>The current record remains current after you call the <legacyBold>Update</legacyBold> or <legacyBold>UpdateBatch</legacyBold> methods.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="31fc53d0-97de-4315-a87b-3bf5cdd1f432">Immediate Mode</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0cb548e0-fcb4-4c49-98c8-be287911f826">Batch Mode</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="74ab6706-e2dc-42cb-af77-dbc58a9cf4ce">Transaction Processing</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>