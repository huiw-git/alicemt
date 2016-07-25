---
title: "Recordset Positioning"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
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
# Recordset Positioning
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the <legacyBold>AbsolutePosition</legacyBold> property to move to a record, based on its ordinal position in the <legacyBold>Recordset</legacyBold> object, or to determine the ordinal position of the current record. The provider must support the appropriate functionality for this property to be available.</para>
    <para>         <legacyBold>AbsolutePosition</legacyBold> is 1-based and equals 1 when the current record is the first record in the <legacyBold>Recordset</legacyBold>. As mentioned previously, you can obtain the total number of records in the <legacyBold>Recordset</legacyBold> object from the <legacyBold>RecordCount</legacyBold> property.</para>
    <para>When you set the <legacyBold>AbsolutePosition</legacyBold> property, even if it is to a record in the current cache, ADO reloads the cache with a new group of records starting with the record you specified. The <legacyBold>CacheSize</legacyBold> property determines the size of this group.</para>
    <alert class="note">
      <para>You should not use the <legacyBold>AbsolutePosition</legacyBold> property as a surrogate record number. The position of a given record changes when you delete a preceding record. There also is no assurance that a given record will have the same <legacyBold>AbsolutePosition</legacyBold> if the <legacyBold>Recordset</legacyBold> object is requeried or reopened. Bookmarks are the recommended way of retaining and returning to a given position and are the only way of positioning across all types of <legacyBold>Recordset</legacyBold> objects.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>