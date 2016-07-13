---
title: SQLInstallTranslator Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLInstallTranslator
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLInstallTranslator Function
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
          <para>Version Introduced: ODBC 2.5, Deprecated</para>
        </definition>
        <definedTerm>
          <legacyBold>Summary</legacyBold>
        </definedTerm>
        <definition>
          <para>In ODBC 3.0, <legacyBold>SQLInstallTranslator</legacyBold> has been replaced by <legacyLink xlink:href="a0630602-53c1-4db0-98ce-70d160aedf8d">SQLInstallTranslatorEx</legacyLink>. Calls to <legacyBold>SQLInstallTranslator</legacyBold> will be mapped to <legacyBold>SQLInstallTranslatorEx</legacyBold>. For more information, see <legacyBold>SQLInstallTranslatorEx</legacyBold>.</para>
          <para>
            <legacyBold>SQLInstallTranslator</legacyBold> will return FALSE if an application calls it in the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager with the <legacyItalic>lpszInfFile</legacyItalic> argument set to a value other than NULL. The Odbc.inf file used in ODBC 2.<legacyItalic>x</legacyItalic> is no longer supported in ODBC 3<legacyItalic>.x</legacyItalic>, even for backward compatibility. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>