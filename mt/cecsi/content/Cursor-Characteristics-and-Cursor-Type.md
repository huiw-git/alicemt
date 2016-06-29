---
title: Cursor Characteristics and Cursor Type
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
translation.priority.ht: 
  - en-gb
---
# Cursor Characteristics and Cursor Type
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application can specify the characteristics of a cursor instead of specifying the cursor type (forward-only, static, keyset-driven, or dynamic). To do this, the application selects the cursor's scrollability (by setting the SQL_ATTR_CURSOR_SCROLLABLE statement attribute) and sensitivity (by setting the SQL_ATTR_CURSOR_SENSITIVITY statement attribute) before opening the cursor on the statement handle. The driver then chooses the cursor type that most efficiently provides the characteristics that the application requested.</para>
    <para>Whenever an application sets any of the statement attributes SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY, or SQL_ATTR_CURSOR_TYPE, the driver makes any required change to the other statement attributes in this set of four attributes so that their values remain consistent. As a result, when the application specifies a cursor characteristic, the driver can change the attribute that indicates cursor type based on this implicit selection; when the application specifies a type, the driver can change any of the other attributes to be consistent with the characteristics of the selected type. For more information about these statement attributes, see the <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink> function description.</para>
    <para>An application that sets statement attributes to specify both a cursor type and cursor characteristics runs the risk of obtaining a cursor that is not the most efficient method available on that driver of meeting the application's requirements.</para>
    <para>The implicit setting of statement attributes is driver-defined except that it must follow these rules:  </para>
    <list class="bullet">
      <listItem>
        <para>Forward-only cursors are never scrollable; see the definition of SQL_ATTR_CURSOR_SCROLLABLE in <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Insensitive cursors are never updatable (and thus their concurrency is read-only); this is based on their definition of insensitive cursors in the ISO SQL standard.</para>
      </listItem>
    </list>
    <para>Consequently, the implicit setting of statement attributes occurs in the cases described in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Application sets attribute to</para>
          </TD>
          <TD>
            <para>Other attributes set implicitly</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ATTR_CONCURRENCY to SQL_CONCUR_READ_ONLY</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CURSOR_SENSITIVITY to SQL_INSENSITIVE.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CONCURRENCY to SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER, or SQL_CONCUR_VALUES</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CURSOR_SENSITIVITY to SQL_UNSPECIFIED or SQL_SENSITIVE, as defined by the driver. It can never be set to SQL_INSENSITIVE, because insensitive cursors are always read-only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_SCROLLABLE to SQL_NONSCROLLABLE</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_FORWARD_ONLY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_SCROLLABLE to SQL_SCROLLABLE</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN, or SQL_CURSOR_DYNAMIC, as specified by the driver. It is never set to SQL_CURSOR_FORWARD_ONLY.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_SENSITIVITY to SQL_INSENSITIVE</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CONCURRENCY to SQL_CONCUR_READ_ONLY.</para>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_STATIC.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_SENSITIVITY to SQL_SENSITIVE</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CONCURRENCY to SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER, or SQL_CONCUR_VALUES, as specified by the driver. It is never set to SQL_CONCUR_READ_ONLY.</para>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN, or SQL_CURSOR_DYNAMIC, as specified by the driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_SENSITIVITY to SQL_UNSPECIFIED</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CONCURRENCY to SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER, or SQL_CONCUR_VALUES, as specified by the driver.</para>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN, or SQL_CURSOR_DYNAMIC, as specified by the driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_DYNAMIC</para>
          </TD>
          <TD>
            <para>SQL_ATTR_SCROLLABLE to SQL_SCROLLABLE.</para>
            <para>SQL_ATTR_CURSOR_SENSITIVITY to SQL_SENSITIVE. (But only if SQL_ATTR_CONCURRENCY is not equal to SQL_CONCUR_READ_ONLY. Updatable dynamic cursors are always sensitive to changes that were made in their own transaction.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_FORWARD_ONLY</para>
          </TD>
          <TD>
            <para>SQL_ATTR_CURSOR_SCROLLABLE to SQL_NONSCROLLABLE.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_KEYSET_DRIVEN</para>
          </TD>
          <TD>
            <para>SQL_ATTR_SCROLLABLE to SQL_SCROLLABLE.</para>
            <para>SQL_ATTR_SENSITIVITY to SQL_UNSPECIFIED or SQL_SENSITIVE (according to driver-defined criteria, if SQL_ATTR_CONCURRENCY is not SQL_CONCUR_READ_ONLY).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_STATIC</para>
          </TD>
          <TD>
            <para>SQL_ATTR_SCROLLABLE to SQL_SCROLLABLE.</para>
            <para>SQL_ATTR_SENSITIVITY to SQL_INSENSITIVE (if SQL_ATTR_CONCURRENCY is SQL_CONCUR_READ_ONLY).</para>
            <para>SQL_ATTR_SENSITIVITY to SQL_UNSPECIFIED or SQL_SENSITIVE (if SQL_ATTR_CONCURRENCY is not SQL_CONCUR_READ_ONLY).</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>