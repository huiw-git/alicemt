---
title: Was a Result Set Created?
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4a83b8cb-2d57-4e64-b497-80bd587ee1f9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Was a Result Set Created?
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In most situations, application programmers know whether the statements their application executes will create a result set. This is the case if the application uses hard-coded SQL statements written by the programmer. It is usually the case when the application constructs SQL statements at run time: The programmer can easily include code that flags whether a <legacyBold>SELECT</legacyBold> statement or an <legacyBold>INSERT</legacyBold> statement is being constructed. In a few situations, the programmer cannot possibly know whether a statement will create a result set. This is true if the application provides a way for the user to enter and execute an SQL statement. It is also true when the application constructs a statement at run time to execute a procedure.</para>
    <para>In such cases, the application calls <legacyBold>SQLNumResultCols</legacyBold> to determine the number of columns in the result set. If this is 0, the statement did not create a result set; if it is any other number, the statement did create a result set.</para>
    <para>The application can call <legacyBold>SQLNumResultCols</legacyBold> at any time after the statement is prepared or executed. However, because some data sources cannot easily describe the result sets that will be created by prepared statements, performance will suffer if <legacyBold>SQLNumResultCols</legacyBold> is called after a statement is prepared but before it is executed.</para>
    <para>Some data sources also support determining the number of rows that an SQL statement returns in a result set. To do so, the application calls <legacyBold>SQLRowCount</legacyBold>. Exactly what the row count represents is indicated by the setting of the SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2, or SQL_STATIC_CURSOR_ATTRIBUTES2 option (depending on the type of the cursor) returned by a call to <legacyBold>SQLGetInfo</legacyBold>. This bitmask indicates for each cursor type whether the row count returned is exact, approximate, or is not available at all. Whether row counts for static or keyset-driven cursors are affected by changes made through <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>, or by positioned update or delete statements, depends on other bits returned by the same option arguments listed previously. For more information, see the <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>