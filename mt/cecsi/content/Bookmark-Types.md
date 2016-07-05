---
title: Bookmark Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
translation.priority.ht: 
  - en-gb
---
# Bookmark Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>All bookmarks in ODBC 3<legacyItalic>.x</legacyItalic> are variable-length bookmarks. This allows a primary key or a unique index associated with a table to be used as a bookmark. The bookmark also can be a 32-bit value, as was used in ODBC 2.<legacyItalic>x</legacyItalic>. To specify that a bookmark is used with a cursor, an ODBC 3<legacyItalic>.x</legacyItalic> application sets the SQL_ATTR_USE_BOOKMARK statement attribute to SQL_UB_VARIABLE. A variable-length bookmark is automatically used.</para>
    <para>An application can call <legacyBold>SQLColAttribute</legacyBold> with the <legacyItalic>FieldIdentifier</legacyItalic> argument set to SQL_DESC_OCTET_LENGTH to obtain the length of the bookmark. Because a variable-length bookmark can be a long value, an application should not bind to column 0 unless it will use the bookmark for many of the rows in the rowset.</para>
    <para>Fixed-length bookmarks are supported only for backward compatibility. If an ODBC 2.<legacyItalic>x</legacyItalic> application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver calls <legacyBold>SQLSetStmtOption</legacyBold> to set SQL_USE_BOOKMARKS to SQL_UB_ON, it is mapped in the Driver Manager to SQL_UB_VARIABLE. A variable-length bookmark is used, even if only 32 bits of it are populated. If a driver supports fixed-length bookmarks, it will support variable-length bookmarks. If an ODBC 3<legacyItalic>.x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_USE_BOOKMARKS to SQL_UB_VARIABLE, it is mapped in the Driver Manager to SQL_UB_ON and a 32-bit fixed-length bookmark is used. The SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute must then point to a 32-bit bookmark. If the bookmarks used are longer than 32 bits, such as when primary keys are used as bookmarks, the cursor must map the actual values to 32-bit values. It could, for example, build a hash table of them. When an ODBC 3<legacyItalic>.x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver binds a bookmark, the buffer length must be 4.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>