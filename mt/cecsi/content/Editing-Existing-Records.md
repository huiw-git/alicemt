---
title: "Editing Existing Records"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
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
# Editing Existing Records
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To edit existing records, move to the row you want to edit and change the <legacyBold>Value</legacyBold> property of the fields you want to change. For more information about the <legacyBold>Field</legacyBold> object's <legacyBold>Value</legacyBold> property, see <legacyLink xlink:href="de1d74af-89b6-4f3f-a8c9-07c3e2b3c9a5">Examining Data</legacyLink>. Depending on your cursor type, you will use <legacyBold>Update</legacyBold> or <legacyBold>UpdateBatch</legacyBold> to send changes back to the data source. For more information, see <legacyLink xlink:href="8dc27274-4f96-43d1-913c-4ff7d01b9a27">Updating and Persisting Data</legacyLink>.</para>
    <para>It is usually more efficient to use a stored procedure with a command object to perform updates, as well as to perform other operations, because a stored procedure does not require the creation of a cursor. For more information about cursors, see <legacyLink xlink:href="c1b7d7e6-1707-4ce2-863f-0c6dea967df6">Understanding Cursors and Locks</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>