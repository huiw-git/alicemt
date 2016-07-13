---
title: SQLTransact Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLTransact
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLTransact Function
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
          <para>In ODBC 3.<legacyItalic>x</legacyItalic>, the ODBC 2<legacyItalic>.x</legacyItalic> function <legacyBold>SQLTransact</legacyBold> has been replaced by <legacyBold>SQLEndTran</legacyBold>. For more information, see <legacyLink xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</legacyLink>.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>The attribute SQL_ASYNC_DBC_FUNCTION_ENABLE, which was introduced in ODBC 3.8, is not supported by <unmanagedCodeEntityReference>SQLTransact</unmanagedCodeEntityReference>. Applications using an asynchronous operation on a connection handle must use <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference>.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>