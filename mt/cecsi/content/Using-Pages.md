---
title: "Using Pages"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
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
# Using Pages
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the <legacyBold>PageCount</legacyBold> property to determine how many pages of data are in the <legacyBold>Recordset</legacyBold> object. <legacyItalic>Pages</legacyItalic> are groups of records whose size equals the <legacyBold>PageSize</legacyBold> property setting. Even if the last page is incomplete because there are fewer records than the <legacyBold>PageSize</legacyBold> value, it counts as an additional page in the <legacyBold>PageCount</legacyBold> value. If the <legacyBold>Recordset</legacyBold> object does not support this property, <legacyBold>PageCount</legacyBold> will be -1 to indicate that the <legacyBold>PageCount</legacyBold> is indeterminable.</para>
    <para>Use the <legacyBold>PageSize</legacyBold> property to determine how many records make up a logical page of data. Establishing a page size allows you to use the <legacyBold>AbsolutePage</legacyBold> property to move to the first record of a particular page. This is useful in Web-server scenarios when you want to allow the user to page through data, viewing a certain number of records at a time.</para>
    <para>This property can be set at any time, and its value will be used for calculating the location of the first record of a particular page.</para>
    <para>Use the <legacyBold>AbsolutePage</legacyBold> property to identify the page number on which the current record is located. Again, the provider must support the appropriate functionality for this property to be available.</para>
    <para>         <legacyBold>AbsolutePage</legacyBold> is 1-based and equals 1 when the current record is the first record in the <legacyBold>Recordset</legacyBold>. Set this property to move to the first record of a particular page. Obtain the total number of pages from the <legacyBold>PageCount</legacyBold> property.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>