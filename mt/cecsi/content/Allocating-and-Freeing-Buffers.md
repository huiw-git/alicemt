---
title: Allocating and Freeing Buffers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 886bc9ed-39d4-43d2-82ff-aebc35b14d39
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Allocating and Freeing Buffers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>All buffers are allocated and freed by the application. If a buffer is not deferred, it need only exist for the duration of the call to a function. For example, <legacyBold>SQLGetInfo</legacyBold> returns the value associated with a particular option in the buffer pointed to by the <legacyItalic>InfoValuePtr</legacyItalic> argument. This buffer can be freed immediately after the call to <legacyBold>SQLGetInfo</legacyBold>, as shown in the following code example:</para>
    <code>SQLSMALLINT   InfoValueLen;
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.

SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,
            &amp;InfoValueLen);

free(InfoValuePtr);                        // OK to free InfoValuePtr.</code>
    <para>Because deferred buffers are specified in one function and used in another, it is an application programming error to free a deferred buffer while the driver still expects it to exist. For example, the address of the *<legacyItalic>ValuePtr</legacyItalic> buffer is passed to <legacyBold>SQLBindCol</legacyBold> for later use by <legacyBold>SQLFetch</legacyBold>. This buffer cannot be freed until the column is unbound, such as with a call to <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLFreeStmt</legacyBold> as shown in the following code example:</para>
    <code>SQLRETURN    rc;
SQLINTEGER   ValueLenOrInd;
SQLHSTMT     hstmt;

// Allocate ValuePtr
SQLCHAR * ValuePtr = malloc(50);

// Bind ValuePtr to column 1. It is an error to free ValuePtr here.
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, 50, &amp;ValueLenOrInd);

// Fetch each row of data and place the value for column 1 in *ValuePtr.
// Code to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO 
// not shown.
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {
   // It is an error to free ValuePtr here.
}

// Unbind ValuePtr from column 1.  It is now OK to free ValuePtr.
SQLFreeStmt(hstmt, SQL_UNBIND);
free(ValuePtr);</code>
    <para>Such an error is easily made by declaring the buffer locally in a function; the buffer is freed when the application leaves the function. For example, the following code causes undefined and probably fatal behavior in the driver:</para>
    <code>SQLRETURN   rc;
SQLHSTMT    hstmt;

BindAColumn(hstmt);

// Fetch each row of data and try to place the value for column 1 in
// *ValuePtr. Because ValuePtr has been freed, the behavior is undefined
// and probably fatal. Code to check if rc equals SQL_ERROR or 
// SQL_SUCCESS_WITH_INFO not shown.
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {}

   .
   .
   .

void BindAColumn(SQLHSTMT hstmt)  // WARNING! This function won't work!
{
   // Declare ValuePtr locally.
   SQLCHAR      ValuePtr[50];
   SQLINTEGER   ValueLenOrInd;

   // Bind rgbValue to column.
   SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr),
               &amp;ValueLenOrInd);

   // ValuePtr is freed when BindAColumn exits.
}</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>