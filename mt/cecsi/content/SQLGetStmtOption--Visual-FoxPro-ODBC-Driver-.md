---
title: SQLGetStmtOption (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
translation.priority.ht: 
  - en-gb
---
# SQLGetStmtOption (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Level One</para>
    <para>Returns the current setting of a statement option.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>                 <legacyItalic>FOption</legacyItalic>               </para>
          </TD>
          <TD>
            <para>Returns</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_GET_BOOKMARK</para>
          </TD>
          <TD>
            <para>32-bit integer value that is the bookmark for the current record number</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_NUMBER</para>
          </TD>
          <TD>
            <para>32-bit integer specifying the position of the current row within the result set</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TRANSLATE_DLL</para>
          </TD>
          <TD>
            <para>Error: "Driver not capable"</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The Visual FoxPro ODBC Driver has no translation DLLs.</para>
    <para>For more information, see <legacyLink xlink:href="d69c2668-4260-4722-8c34-1c51caac307f">SQLGetStmtOption</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>