---
title: SQLError (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLError (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Core Level</para>
    <para>Returns error or status information about the last error. The driver maintains a stack or list of errors that can be returned for the <legacyItalic>hstmt</legacyItalic>, <legacyItalic>hdbc</legacyItalic>, and <legacyItalic>henv </legacyItalic>arguments, depending on how the call to <legacyBold>SQLError</legacyBold> is made. The error queue is flushed after each statement.</para>
    <para>The following table describes the <legacyBold>SQLError</legacyBold> arguments and return values used by the driver.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQLError argument</para>
          </TD>
          <TD>
            <para>Return value description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyItalic>szSQLState</legacyItalic>             </para>
          </TD>
          <TD>
            <para>The value for the SQLSTATE represented by the error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>pfNativeError</legacyItalic>             </para>
          </TD>
          <TD>
            <para>A nonzero value indicates a <legacyLink xlink:href="7b2622e8-ccee-4853-9171-4fb10de0461d">Visual FoxPro ODBC Driver Native Error Message</legacyLink>. A value of zero indicates the error has been detected by the driver and mapped to the appropriate <legacyLink xlink:href="9b4251f2-6fa6-49df-8abf-7cc1cc35d1c8">ODBC Error Code</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>szErrorMsg</legacyItalic>             </para>
          </TD>
          <TD>
            <para>The text for the native error or ODBC error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>pcbErrorMsg</legacyItalic>             </para>
          </TD>
          <TD>
            <para>The length of the message text plus the length of the identifiers.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For more information on driver error messages, see <legacyLink xlink:href="58ea9734-4edf-44da-ba80-938aa7b340e4">Error Messages Overview</legacyLink>. For more information about this function, see <legacyLink xlink:href="ee5c90de-3c61-4f63-8b57-1543d1704a0e">SQLError</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>