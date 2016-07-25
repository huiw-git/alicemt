---
title: "Receiving Multiple Recordsets"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
caps.latest.revision: 14
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
# Receiving Multiple Recordsets
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyLink xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">Microsoft OLE DB Provider for SQL Server</legacyLink> supports returning multiple <legacyBold>Recordset</legacyBold> objects for a single command containing multiple SQL statements, one <legacyBold>Recordset</legacyBold> per SQL statement. The order in which the <legacyBold>Recordset</legacyBold>s are returned follows the order in which the SQL statements are placed in the command text. </para>
    <para>The Microsoft OLE DB Provider for SQL Server also returns multiple resultsets to ADO when the command contains a COMPUTE clause. For example, a command containing the following SQL statement will return the results in two <legacyBold>Recordset</legacyBold> objects: one for the rowset of (<legacyItalic>ProductID</legacyItalic>, <legacyItalic>ProductName</legacyItalic>, <legacyItalic>UnitPrice</legacyItalic>), and the other for the average price of all products in the table. </para>
    <code>SELECT ProductID, ProductName, UnitPrice 
  FROM PRODUCTS 
  COMPUTE AVG(UnitPrice)</code>
    <para>You can use the <legacyBold>Recordset.NextRecordset</legacyBold> method to enumerate the two <?Comment JT: Used to contain two subtopics that were lost, and so links were deleted. 2006-06-27T14:04:00Z  Id='0?>objects<?CommentEnd Id='0'
    ?>.</para>
    <para>For more information, see <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>