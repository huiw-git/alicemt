---
title: Desktop Database Driver Compatibility
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Desktop Database Driver Compatibility
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Unicode is a method of software character encoding that treats all characters as having a fixed width of two bytes. This method is used as an alternative to Windows ANSI character encoding, which, because it represents characters in one byte, is limited to 256 characters. Because Unicode can represent over 65,000 characters, it accommodates many languages whose characters are not represented in ANSI encoding. </para>
    <para>The ODBC 3.5 (or later) Driver Manager is Unicode-enabled. This affects two major areas: function calls and string data types. The Driver Manager maps function string arguments and string data as required by the application and driver, both of which can be either Unicode-enabled or ANSI-enabled. </para>
    <para>The ODBC 3.5 (or later) Driver Manager supports the use of a Unicode driver with both a Unicode application and an ANSI application. It also supports the use of an ANSI driver with an ANSI application. The Driver Manager provides limited Unicode-to-ANSI mapping for a Unicode application working with an ANSI driver. This allows access to the Jet 3.5 databases and support of all existing ISAM file types.</para>
    <para>When an ANSI application uses the ODBC Desktop Database Driver 4.0 and accesses Microsoft Access 4.0 or later, the driver exposes the data type as SQL_CHAR, SQL_VARCHAR, or SQL_LONGVARCHAR even though Jet 4.0 supports the wide version. Older versions of Jet do not support SQL_WCHAR, SQL_WVARCHAR, and SQL_WLONGVARCHAR. This restriction also applies in cases where the old formats are used with the Jet 4.0 Database Engine.</para>
    <para>For more information concerning Unicode issues with ODBC, see <legacyLink xlink:href="113e1c9a-8333-4805-86f2-e4b57ab816a5">Unicode</legacyLink> in Programming Considerations. </para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>