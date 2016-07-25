---
title: "Duplicated Features"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Duplicated Features
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following ODBC 2.<legacyItalic>x</legacyItalic> functions have been duplicated by ODBC 3.<legacyItalic>x</legacyItalic> functions. As a result, the ODBC 2.<legacyItalic>x</legacyItalic> functions are deprecated in ODBC 3.<legacyItalic>x</legacyItalic>. The ODBC 3.<legacyItalic>x</legacyItalic> functions are referred to as replacement functions.</para>
    <para>When an application uses a deprecated ODBC 2.<legacyItalic>x</legacyItalic> function and the underlying driver is an ODBC 3.<legacyItalic>x</legacyItalic> driver, the Driver Manager maps the function call to the corresponding replacement function. The only exception to this rule is <legacyBold>SQLExtendedFetch</legacyBold>. (See the footnote at the end of the following table.) For more information about these mappings, see <legacyLink xlink:href="ee462617-1d79-4c88-afeb-b129cff34cc6">Mapping Deprecated Functions</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
    <para>When an application uses a replacement function and the underlying driver is an ODBC 2.<legacyItalic>x </legacyItalic>driver, the Driver Manager maps the function call to the corresponding deprecated function.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC 2.<legacyItalic>x</legacyItalic> function</para>
          </TD>
          <TD>
            <para>ODBC 3.<legacyItalic>x</legacyItalic> function</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>SQLAllocConnect</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLAllocHandle</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLAllocEnv</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLAllocHandle</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLAllocStmt</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLAllocHandle</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColAttributes</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLColAttribute</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLError</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLGetDiagRec</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLExtendedFetch</legacyBold>[1]</para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLFetchScroll</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFreeConnect</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLFreeHandle</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLFreeEnv</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLFreeHandle</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetConnectOption</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLGetConnectAttr</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetStmtOption</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLGetStmtAttr</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLParamOptions</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLSetStmtAttr</legacyBold>, <legacyBold>SQLGetStmtAttr</legacyBold></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetConnectOption</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLSetConnectAttr</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetParam</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLBindParameter</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSetStmtOption</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLSetStmtAttr</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLTransact</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLEndTran</legacyBold>             </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   The function <legacyBold>SQLExtendedFetch</legacyBold> is duplicated functionality; <legacyBold>SQLFetchScroll</legacyBold> provides the same functionality in ODBC 3.<legacyItalic>x</legacyItalic>. However, the Driver Manager does not map <legacyBold>SQLExtendedFetch</legacyBold> to <legacyBold>SQLFetchScroll</legacyBold> when going against an ODBC 3.<legacyItalic>x</legacyItalic> driver. For more information, see <legacyLink xlink:href="57f65c38-d9ee-46c8-9051-128224a582c6">What the Driver Manager Does</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility. The Driver Manager maps <legacyBold>SQLFetchScroll</legacyBold> to <legacyBold>SQLExtendedFetch</legacyBold> when going against an ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
    <alert class="note">
      <para>The function <legacyBold>SQLBindParam</legacyBold> is a special case. <legacyBold>SQLBindParam</legacyBold> is duplicated functionality. This is not an ODBC 2<legacyItalic>.x </legacyItalic>function, but a function that is present in the Open Group and ISO standards. The functionality provided by this function is completely subsumed by that of <legacyBold>SQLBindParameter</legacyBold>. As a result, the Driver Manager maps a call to <legacyBold>SQLBindParam</legacyBold> to <legacyBold>SQLBindParameter</legacyBold> when the underlying driver is an ODBC 3.<legacyItalic>x</legacyItalic> driver. However, when the underlying driver is an ODBC 2<legacyItalic>.x </legacyItalic>driver, the Driver Manager does not perform this mapping.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>