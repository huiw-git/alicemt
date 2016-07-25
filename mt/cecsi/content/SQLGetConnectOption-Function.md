---
title: "SQLGetConnectOption Function"
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
  - SQLGetConnectOption
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
caps.latest.revision: 10
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetConnectOption Function
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
          <para>In ODBC 3<legacyItalic>.x</legacyItalic>, the ODBC 2<legacyItalic>.x</legacyItalic> function <legacyBold>SQLGetConnectOption</legacyBold> has been replaced by <legacyBold>SQLGetConnectAttr</legacyBold>. For more information, see <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr</legacyLink>.</para>
          <alert class="note">
            <para>For more information about what the Driver Manager maps this function to when an ODBC 2<legacyItalic>.x</legacyItalic> application is working with an ODBC 3<legacyItalic>.x</legacyItalic> driver, see <legacyLink xlink:href="ee462617-1d79-4c88-afeb-b129cff34cc6">Mapping Deprecated Functions</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
          </alert>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>The attribute SQL_ASYNC_DBC_FUNCTION_ENABLE introduced in ODBC 3.8 is not supported by <unmanagedCodeEntityReference>SQLGetConnectOption</unmanagedCodeEntityReference>. Applications that use the asynchronous operation on a connection handle must use <unmanagedCodeEntityReference>SQLGetConnectAttr</unmanagedCodeEntityReference>.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>