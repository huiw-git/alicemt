---
title: "Overriding Default Precision and Scale for Numeric Data Types"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Overriding Default Precision and Scale for Numeric Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the SQL_DESC_TYPE field in an ARD is set to SQL_C_NUMERIC, by calling either <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLSetDescField</legacyBold>, the SQL_DESC_SCALE field in the ARD is set to 0 and the SQL_DESC_PRECISION field is set to a driver-defined default precision. This is also true when the SQL_DESC_TYPE field in an APD is set to SQL_C_NUMERIC, by calling either <legacyBold>SQLBindParameter</legacyBold> or <legacyBold>SQLSetDescField</legacyBold>. This is true for input, input/output, or output parameters.</para>
  </introduction>
  <section>
    <content>
      <para>If either of the defaults described previously are not acceptable for an application, the application should set the SQL_DESC_SCALE or SQL_DESC_PRECISION field by calling <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.</para>
      <para>If the application calls <legacyBold>SQLGetData</legacyBold> to return data into an SQL_C_NUMERIC structure, the default SQL_DESC_SCALE and SQL_DESC_PRECISION fields are used. If the defaults are not acceptable, the application must call <legacyBold>SQLSetDescRec</legacyBold> or <legacyBold>SQLSetDescField</legacyBold> to set the fields and then call <legacyBold>SQLGetData</legacyBold> with a <legacyItalic>TargetType</legacyItalic> of SQL_ARD_TYPE to use the values in the descriptor fields.</para>
      <para>When <legacyBold>SQLPutData</legacyBold> is called, the call uses the SQL_DESC_SCALE and SQL_DESC_PRECISION fields of the descriptor record that corresponds to the data-at-execution parameter or column, which are APD fields for calls to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>, or ARD fields for calls to <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>