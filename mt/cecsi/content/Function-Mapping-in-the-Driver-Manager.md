---
title: "Function Mapping in the Driver Manager"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff093b29-671a-4fc0-86c9-08a311a98e54
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Function Mapping in the Driver Manager
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The driver manager supports two entry points for functions that take string arguments. The undecorated function (<legacyBold>SQLDriverConnect</legacyBold>) is the ANSI form of the function. The Unicode form is decorated with a <legacyItalic>W</legacyItalic> (<legacyBold>SQLDriverConnectW</legacyBold>.)</para>
    <para>The ODBC header file also supports functions decorated with an <legacyItalic>A,</legacyItalic> (<legacyBold>SQLDriverConnectA</legacyBold>) for the convenience of mixed ANSI/Unicode applications. Calls made to the <legacyBold>A</legacyBold> functions are actually calls into the undecorated entry point (<legacyBold>SQLDriverConnect</legacyBold>.)</para>
    <para>If the application is compiled with the _UNICODE <legacyBold>#define</legacyBold>, the ODBC header file will map undecorated function calls (<legacyBold>SQLDriverConnect</legacyBold>) to the Unicode version (<legacyBold>SQLDriverConnectW</legacyBold>.)</para>
    <para>The Driver Manager recognizes a driver as a Unicode driver if <legacyBold>SQLConnectW</legacyBold> is supported by the driver.</para>
    <para>If the driver is a Unicode driver, the Driver Manager makes function calls as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>Passes a function without string arguments or parameters directly through to the driver.</para>
      </listItem>
      <listItem>
        <para>Passes Unicode functions (with the <legacyItalic>W</legacyItalic> suffix) directly through to the driver.</para>
      </listItem>
      <listItem>
        <para>Converts an ANSI function (with the <legacyItalic>A</legacyItalic> suffix) to a Unicode function (with the <legacyItalic>W</legacyItalic> suffix) by converting the string arguments into Unicode characters and passes the Unicode function to the driver.</para>
      </listItem>
    </list>
    <para>If the driver is an ANSI driver, the Driver Manager makes function calls as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>Passes functions without string arguments or parameters directly through to the driver.</para>
      </listItem>
      <listItem>
        <para>Converts Unicode functions (with the <legacyItalic>W</legacyItalic> suffix) to an ANSI function call and passes it to the driver.</para>
      </listItem>
      <listItem>
        <para>Passes an ANSI function directly to the driver.</para>
      </listItem>
    </list>
    <para>The Driver Manager is Unicode-enabled internally. As a result, the optimum performance is obtained by a Unicode application working with a Unicode driver, because the Driver Manager simply passes Unicode functions through to the driver. When an ANSI application is working with an ANSI driver, the Driver Manager must convert strings from ANSI to Unicode when processing some functions, such as <legacyBold>SQLDriverConnect</legacyBold>. After processing the function, the Driver Manager must then convert the Unicode string back to ANSI before sending the function to the ANSI driver.</para>
    <para>An application should not modify or read its bound parameter buffers when the driver returns SQL_STILL_EXECUTING or SQL_NEED_DATA. The Driver Manager leaves the buffers bound to ANSI until the driver returns SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, or SQL_ERROR. A multithreaded application should not gain access to any bound parameter values that another thread is executing an SQL statement on. The Driver Manager converts the data from Unicode to ANSI "in place," and the other thread might see ANSI data in these buffers while the driver is still processing the SQL statement. Applications that bind Unicode data to an ANSI driver must not bind two different columns to the same address.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>