---
title: Deleting Rows in the Rowset with SQLSetPos
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Deleting Rows in the Rowset with SQLSetPos
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The delete operation of <legacyBold>SQLSetPos</legacyBold> makes the data source delete one or more selected rows of a table. To delete rows with <legacyBold>SQLSetPos</legacyBold>, the application calls <legacyBold>SQLSetPos</legacyBold> with <legacyItalic>Operation</legacyItalic> set to SQL_DELETE and <legacyItalic>RowNumber</legacyItalic> set to the number of the row to delete. If <legacyItalic>RowNumber</legacyItalic> is 0, all rows in the rowset are deleted. </para>
    <para>After <legacyBold>SQLSetPos</legacyBold> returns, the deleted row is the current row and its status is SQL_ROW_DELETED. The row cannot be used in any further positioned operations, such as calls to <legacyBold>SQLGetData</legacyBold> or <legacyBold>SQLSetPos</legacyBold>.</para>
    <para>When deleting all rows of the rowset (<legacyItalic>RowNumber</legacyItalic> is equal to 0), the application can prevent the driver from deleting certain rows by using the row operation array, in the same way as for the update operation of <legacyBold>SQLSetPos</legacyBold>. (See <legacyLink xlink:href="d83a8c2a-5aa8-4f19-947c-79a817167ee1">Updating Rows in the Rowset with SQLSetPos</legacyLink>.)</para>
    <para>Every row that is deleted should be a row that exists in the result set. If the application buffers were filled by fetching and if a row status array has been maintained, its values at each of these row positions should not be SQL_ROW_DELETED, SQL_ROW_ERROR, or SQL_ROW_NOROW.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>