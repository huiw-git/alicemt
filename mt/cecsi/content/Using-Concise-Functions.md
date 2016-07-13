---
title: Using Concise Functions
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using Concise Functions
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Some ODBC functions gain implicit access to descriptors. Application writers may find them more convenient than calling <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLGetDescField</legacyBold>. These functions are called <legacyItalic>concise</legacyItalic> functions because they perform a number of functions, including setting or getting descriptor fields. Some concise functions let an application set or retrieve several related descriptor fields in a single function call. </para>
    <para>Concise functions can be called without first retrieving a descriptor handle for use as an argument. These functions work with the descriptor fields associated with the statement handle that they are called on.</para>
    <para>The concise functions <legacyBold>SQLBindCol</legacyBold> and <legacyBold>SQLBindParameter</legacyBold> bind a column or parameter by setting the descriptor fields that correspond to their arguments. Each of these functions performs more tasks than simply setting descriptors. <legacyBold>SQLBindCol</legacyBold> and <legacyBold>SQLBindParameter</legacyBold> provide a complete specification of the binding of a data column or dynamic parameter. An application can, however, change individual details of a binding by calling <legacyBold>SQLSetDescField </legacyBold>or <legacyBold>SQLSetDescRec</legacyBold> and can completely bind a column or parameter by making a series of suitable calls to these functions. </para>
    <para>The concise functions<legacyBold> SQLColAttribute</legacyBold>, <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLDescribeParam</legacyBold>, <legacyBold>SQLNumParams</legacyBold>, and <legacyBold>SQLNumResultCols</legacyBold> retrieve values in descriptor fields.</para>
    <para>         <legacyBold>SQLSetDescRec</legacyBold> and <legacyBold>SQLGetDescRec</legacyBold> are concise functions that, with one call, set or get multiple descriptor fields that affect the data type and storage of column or parameter data. <legacyBold>SQLSetDescRec</legacyBold> is an effective way to change the binding of column or parameter data in one step. </para>
    <para>         <legacyBold>SQLSetStmtAttr</legacyBold> and <legacyBold>SQLGetStmtAttr</legacyBold> serve as concise functions in some cases. (See <legacyLink xlink:href="f38623c8-fdd4-4601-b1f0-97c593d31177">Descriptor Fields</legacyLink>.)</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>