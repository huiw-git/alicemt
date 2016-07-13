---
title: SQLSetStmtOption Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetStmtOption
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 9cbe2b62-4cf7-43ab-8fb4-9a53df2c6b3f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetStmtOption Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <content>
      <definitionTable>
        <definedTerm> <legacyBold>Conformance</legacyBold> </definedTerm>
        <definition>
          <para>Version Introduced: ODBC 1.0 Standards Compliance: Deprecated</para>
        </definition>
        <definedTerm> <legacyBold>Summary</legacyBold> </definedTerm>
        <definition>
          <para>In ODBC 3<legacyItalic>.x</legacyItalic>, the ODBC 2.0 function <legacyBold>SQLSetStmtOption</legacyBold> has been replaced by <legacyBold>SQLSetStmtAttr</legacyBold>. For more information, see <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink>.</para>
          <alert class="note">
            <para>For more information about what the Driver Manager maps this function to when an ODBC 2<legacyItalic>.x</legacyItalic> application is working with an ODBC 3<legacyItalic>.x</legacyItalic> driver, see <legacyLink xlink:href="ee462617-1d79-4c88-afeb-b129cff34cc6">Mapping Deprecated Functions</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
          </alert>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>See <link xlink:href="ed9851ce-44ee-4c8e-b626-1d0b52da30fe">ODBC 64-Bit Information</link>, if your application will run on a 64-bit operating system.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>