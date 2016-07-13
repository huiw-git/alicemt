---
title: Overriding Default Leading and Seconds Precision for Interval Data Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Overriding Default Leading and Seconds Precision for Interval Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the SQL_DESC_TYPE field of an ARD is set to a datetime or interval C type, by calling either <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLSetDescField</legacyBold>, the SQL_DESC_PRECISION field (which contains the interval seconds precision) is set to the following defaults:  </para>
    <list class="bullet">
      <listItem>
        <para>6 for timestamp and all interval data types with a second component.</para>
      </listItem>
      <listItem>
        <para>0 for all other data types.</para>
      </listItem>
    </list>
    <para>For all interval data types, the SQL_DESC_DATETIME_INTERVAL_PRECISION descriptor field, which contains the interval leading field precision, is set to a default value of 2.</para>
    <para>When the SQL_DESC_TYPE field in an APD is set to a datetime or interval C type, by calling either <legacyBold>SQLBindParameter</legacyBold> or <legacyBold>SQLSetDescField</legacyBold>, the SQL_DESC_PRECISION and SQL_DESC_DATETIME_INTERVAL_PRECISION fields in the APD are set to the default given previously. This is true for input parameters but not for input/output or output parameters.</para>
    <para>A call to <legacyBold>SQLSetDescRec</legacyBold> sets the interval leading precision to the default but sets the interval seconds precision (in the SQL_DESC_PRECISION field) to the value of its <legacyItalic>Precision</legacyItalic> argument.</para>
    <para>If either of the defaults given previously is not acceptable to an application, the application should set the SQL_DESC_PRECISION or SQL_DESC_DATETIME_INTERVAL_PRECISION field by calling <legacyBold>SQLSetDescField</legacyBold>.</para>
    <para>If the application calls <legacyBold>SQLGetData</legacyBold> to return data into a datetime or interval C type, the default interval leading precision and interval seconds precision are used. If either default is not acceptable, the application must call <legacyBold>SQLSetDescField</legacyBold> to set either descriptor field, or <legacyBold>SQLSetDescRec</legacyBold> to set SQL_DESC_PRECISION. The call to <legacyBold>SQLGetData</legacyBold> should have a <legacyItalic>TargetType</legacyItalic> of SQL_ARD_TYPE to use the values in the descriptor fields.</para>
    <para>When <legacyBold>SQLPutData</legacyBold> is called, the interval leading precision and interval seconds precision are read from the fields of the descriptor record that correspond to the data-at-execution parameter or column, which are APD fields for calls to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>, or ARD fields for calls to <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>