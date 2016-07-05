---
title: Data Buffer Length
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
translation.priority.ht: 
  - en-gb
---
# Data Buffer Length
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The application passes the byte length of the data buffer to the driver in an argument, named <legacyItalic>BufferLength</legacyItalic> or a similar name. For example, in the following call to <legacyBold>SQLBindCol</legacyBold>, the application specifies the length of the <legacyItalic>ValuePtr</legacyItalic> buffer (<legacyBold>sizeof(</legacyBold><legacyItalic>ValuePtr</legacyItalic><legacyBold>)</legacyBold>):</para>
    <code>SQLCHAR      ValuePtr[50];
SQLINTEGER   ValueLenOrInd;
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &amp;ValueLenOrInd);</code>
    <para>A driver will always return the number of bytes, not the number of characters, in the buffer length argument of any function that has an output string argument.</para>
    <para>Data buffer lengths are required only for output buffers; the driver uses them to avoid writing past the end of the buffer. However, the driver checks the data buffer length only when the buffer contains variable-length data, such as character or binary data. If the buffer contains fixed-length data, such as an integer or date structure, the driver ignores the data buffer length and assumes the buffer is large enough to hold the data; that is, it never truncates fixed-length data. It is therefore important for the application to allocate a large enough buffer for fixed-length data.</para>
    <para>When a truncation of non-data output strings occurs (such as the cursor name returned for <legacyBold>SQLGetCursorName</legacyBold>), the returned length in the buffer length argument is the maximum character length possible.</para>
    <para>Data buffer lengths are not required for input buffers because the driver does not write to these buffers.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="849792f1-cb1e-4bc2-b568-c0aff0b66199">Using Length/Indicator Values</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="2825c6e7-b9ff-42fe-84fc-7fb39728ac5d">Data Length, Buffer Length, and Truncation</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3a141cb4-229d-4027-9349-615cb2995e36">Character Data and C Strings</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>