---
title: "SQLSetScrollOptions Function"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetScrollOptions
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
caps.latest.revision: 11
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetScrollOptions Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyBold>Conformance</legacyBold>
        </definedTerm>
        <definition>
          <para>Version Introduced: ODBC 1.0 Standards Compliance: Deprecated</para>
        </definition>
        <definedTerm>
          <legacyBold>Summary</legacyBold>
        </definedTerm>
        <definition>
          <para>In ODBC 3<legacyItalic>.x</legacyItalic>, the ODBC 2.0 function <legacyBold>SQLSetScrollOptions</legacyBold> has been replaced by calls to <legacyBold>SQLGetInfo</legacyBold> and <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
          <alert class="note">
            <para>For more information about what the Driver Manager maps this function to when an ODBC 2<legacyItalic>.x</legacyItalic> application is working with an ODBC 3<legacyItalic>.x</legacyItalic> driver, see <legacyLink xlink:href="ee462617-1d79-4c88-afeb-b129cff34cc6">Mapping Deprecated Functions</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
          </alert>
          <alert class="note">
            <para>When the Driver Manager maps <legacyBold>SQLSetScrollOptions</legacyBold> for an application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver that does not support <legacyBold>SQLSetScrollOptions</legacyBold>, the Driver Manager sets the SQL_ROWSET_SIZE statement option, not the SQL_ATTR_ROW_ARRAY_SIZE statement attribute, to the <legacyItalic>RowsetSize</legacyItalic> argument in <legacyBold>SQLSetScrollOption</legacyBold>. As a result, <legacyBold>SQLSetScrollOptions</legacyBold> cannot be used by an application when fetching multiple rows by a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. It can be used only when fetching multiple rows by a call to <legacyBold>SQLExtendedFetch</legacyBold>.</para>
          </alert>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>If your application will run on a 64-bit operating system, see <link xlink:href="ed9851ce-44ee-4c8e-b626-1d0b52da30fe">ODBC 64-Bit Information</link>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>