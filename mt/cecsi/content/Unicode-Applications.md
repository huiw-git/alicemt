---
title: Unicode Applications
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Unicode Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can recompile an application as a Unicode application in one of two ways:  </para>
    <list class="bullet">
      <listItem>
        <para>Include the Unicode <legacyBold>#define</legacyBold> contained in the Sqlucode.h header file in the application.</para>
      </listItem>
      <listItem>
        <para>Compile the application with the compiler's Unicode option. (This option will be different for different compilers.)</para>
      </listItem>
    </list>
    <para>To convert an ANSI application to a Unicode application, write the application to store and pass Unicode data. In addition, calls to functions that support SQLPOINTER arguments must be converted to use count of bytes.</para>
    <para>After an application is compiled as a Unicode application, if the application calls an ODBC API function (without a suffix), the Driver Manager recognizes the application as a Unicode application and converts the function call to a Unicode function (with the <legacyItalic>W</legacyItalic> suffix) if the underlying driver supports Unicode. When an ANSI application makes a function call without a suffix, the Driver Manager converts it to ANSI if the underlying driver supports ANSI. If both the application and the driver support the same character encoding, the driver manager passes the calls through to the driver (with certain exceptions for ANSI applications).</para>
    <para>An application can call both Unicode functions (with the <legacyItalic>W</legacyItalic> suffix) and ANSI functions (with or without the <legacyItalic>A</legacyItalic> suffix). Unicode and ANSI function calls can be mixed. If the cursor library is to be used, however, Unicode and ANSI function calls cannot be mixed. The cursor library is either Unicode or ANSI, not a mixture.</para>
    <para>An application can be written such that it can be compiled as either a Unicode application or an ANSI application. In this case, character data types can be declared as SQL_C_TCHAR. This is a macro that inserts SQL_C_WCHAR if the application is compiled as a Unicode application or inserts SQL_C_CHAR if it is compiled as an ANSI application. The application programmer must be careful of functions that take SQLPOINTER as their argument, because the size of the length argument will change (for string data types) depending on whether the application is ANSI or Unicode.</para>
    <para>A function can be called in one of three ways: as a Unicode-only function call (with the <legacyItalic>W</legacyItalic> suffix), as an ANSI-only function call (with the <legacyItalic>A</legacyItalic> suffix), or as the ODBC function call with no suffix. The arguments to the three forms of a function are identical. Only those functions with SQLCHAR * arguments or SQLPOINTER arguments that point to strings require Unicode and ANSI forms. For functions that have arguments that can be declared as a character type, such as <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData</legacyBold> (which do not have Unicode and ANSI forms), the argument can be declared as the Unicode type, the ANSI type, or in the case of a C type argument, the SQL_C_TCHAR macro. For more information, see <legacyLink xlink:href="abc28718-e6d9-49fb-97ff-402d50c3c375">Unicode Data</legacyLink>.</para>
    <para>An application can be written as a Unicode application even if no Unicode drivers are available for it to work with. The Driver Manager will map Unicode functions and data types to ANSI. There are some restrictions to the Unicode to ANSI mappings that can be performed. The existence of a Unicode driver for the Unicode application to work with will result in better performance and will remove the restrictions inherent in the Unicode to ANSI mappings.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>