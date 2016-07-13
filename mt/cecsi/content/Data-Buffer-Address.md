---
title: Data Buffer Address
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Data Buffer Address
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The application passes the address of the data buffer to the driver in an argument, often named <legacyItalic>ValuePtr</legacyItalic> or a similar name. For example, in the following call to <legacyBold>SQLBindCol</legacyBold>, the application specifies the address of the <legacyItalic>Date</legacyItalic> variable:</para>
    <code>SQL_DATE_STRUCT Date;
SQLINTEGER DateInd;
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &amp;dsDate, 0, &amp;DateInd);</code>
    <para>As mentioned in the <legacyLink xlink:href="886bc9ed-39d4-43d2-82ff-aebc35b14d39">Allocating and Freeing Buffers</legacyLink> section, the address of a deferred buffer must remain valid until the buffer is unbound.</para>
    <para>Unless it is specifically prohibited, the address of a data buffer can be a null pointer. For buffers used to send data to the driver, this causes the driver to ignore the information normally contained in the buffer. For buffers used to retrieve data from the driver, this causes the driver to not return a value. In both cases, the driver ignores the corresponding data buffer length argument.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>