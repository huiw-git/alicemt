---
title: SQLRemoveDefaultDataSource Function
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
  - SQLRemoveDefaultDataSource
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: db803266-57df-4864-a41b-901247549c1f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLRemoveDefaultDataSource Function
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
          <para>Version Introduced: ODBC 1.0, Deprecated</para>
        </definition>
        <definedTerm>
          <legacyBold>Summary</legacyBold>
        </definedTerm>
        <definition>
          <para>In ODBC 3.0, the <legacyBold>SQLRemoveDefaultDataSource</legacyBold> function has been replaced by a call to <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource</legacyLink> with an <legacyItalic>fRequest</legacyItalic> argument of ODBC_REMOVE_DEFAULT_DSN. If an ODBC 2<legacyItalic>.x</legacyItalic> installation program calls this function, the ODBC installer will map it to the following <legacyBold>SQLConfigDataSource</legacyBold> call:  </para>
          <code>SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)</code>
        </definition>
      </definitionTable>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>