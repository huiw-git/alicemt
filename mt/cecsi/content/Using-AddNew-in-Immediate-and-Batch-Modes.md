---
title: "Using AddNew in Immediate and Batch Modes"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
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
# Using AddNew in Immediate and Batch Modes
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The behavior of the <legacyBold>AddNew</legacyBold> method depends on the updating mode of the <legacyBold>Recordset</legacyBold> object and whether you pass the <legacyItalic>FieldList</legacyItalic> and <legacyItalic>Values</legacyItalic> arguments.</para>
    <para>In immediate update mode (in which the provider writes changes to the underlying data source once you call the <legacyBold>Update</legacyBold> method), calling the <legacyBold>AddNew</legacyBold> method without arguments sets the <legacyBold>EditMode</legacyBold> property to <legacyBold>adEditAdd.</legacyBold> The provider caches any field value changes locally. Calling the <legacyBold>Update</legacyBold> method posts the new record to the database and resets the <legacyBold>EditMode</legacyBold> property to <legacyBold>adEditNone.</legacyBold> If you pass the <legacyItalic>FieldList</legacyItalic> and <legacyItalic>Values</legacyItalic> arguments, ADO immediately posts the new record to the database (no <legacyBold>Update</legacyBold> call is necessary); the <legacyBold>EditMode</legacyBold> property value does not change (<legacyBold>adEditNone</legacyBold>).</para>
    <para>In batch update mode, calling the <legacyBold>AddNew</legacyBold> method without arguments sets the <legacyBold>EditMode</legacyBold> property to <legacyBold>adEditAdd</legacyBold>. The provider caches any field value changes locally. Calling the <legacyBold>Update</legacyBold> method adds the new record to the current <legacyBold>Recordset</legacyBold> and resets the <legacyBold>EditMode</legacyBold> property to <legacyBold>adEditNone</legacyBold>, but the provider does not post the changes to the underlying database until you call the <legacyBold>UpdateBatch</legacyBold> method. If you pass the <legacyItalic>FieldList</legacyItalic> and <legacyItalic>Values</legacyItalic> arguments, ADO sends the new record to the provider for storage in a cache; you need to call the <legacyBold>UpdateBatch</legacyBold> method to post the new record to the underlying database. For more information about <legacyBold>Update</legacyBold> and <legacyBold>UpdateBatch</legacyBold>, see <legacyLink xlink:href="8dc27274-4f96-43d1-913c-4ff7d01b9a27">Updating and Persisting Data</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>