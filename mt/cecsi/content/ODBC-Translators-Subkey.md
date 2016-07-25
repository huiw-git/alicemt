---
title: "ODBC Translators Subkey"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Translators Subkey
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The values under the ODBC Translators subkey list the installed translators. The format of these values is shown in the following table.</para>
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
            <para>               <legacyItalic>translator-desc</legacyItalic>             </para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyBold>Installed</legacyBold>             </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The <legacyItalic>translator-desc</legacyItalic> name is defined by the translator developer.</para>
    <para>For example, suppose a user has installed the Microsoft® Code Page Translator and a custom ASCII to EBCDIC translator. The values under the ODBC Translators subkey might be as follows:</para>
    <code>MS Code Page Translator: REG_SZ : Installed
ASCII to EBCDIC: REG_SZ : Installed.</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>