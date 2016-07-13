---
title: ODBC Core Subkey
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Core Subkey
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The value under the ODBC Core subkey gives the usage count for the core components (Driver Manager, cursor library, installer DLL, and so on). The format of this value is shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>Data type</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>UsageCount</para>
          </TD>
          <TD>
            <para>REG_DWORD</para>
          </TD>
          <TD>
            <para>               <legacyItalic>count</legacyItalic>             </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For example, suppose the ODBC Core components have been installed by the setup programs for three different applications and two different drivers. The value under the ODBC Core subkey would be:</para>
    <code>UsageCount : REG_DWORD : 0x5</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>