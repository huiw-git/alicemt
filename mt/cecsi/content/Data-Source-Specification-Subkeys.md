---
title: Data Source Specification Subkeys
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Data Source Specification Subkeys
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each data source listed in the ODBC Data Sources subkey has a subkey of its own. This subkey has the same name as the corresponding value under the ODBC Data Sources subkey. The values under this subkey must list the driver DLL and may list a description of the data source. If the driver supports translators, the values may list the name of a default translator, the default translation DLL, and the default translation option. The values may also list other information required by the driver to connect to the data source. For example, the driver might require a server name, database name, or schema name.</para>
    <para>The formats of the values are as shown in the following table. Only the Driver value is required.</para>
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
            <para>Description</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyItalic>description</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Driver</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyItalic>driver-DLL-path</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TranslationDLL</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyItalic>translator-DLL-path</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TranslationName</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyItalic>translator-name</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TranslationOption</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyItalic>translation-option</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>opt-value-name</legacyItalic>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>opt-value-type</legacyItalic>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>opt-value-data</legacyItalic>             </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For example, suppose the SQL Server driver requires the server name and a flag for OEM to ANSI conversion and defines the Server and OEMTOANSI values for these. Suppose also that the Inventory data source uses the Microsoft® Code Page Translator to translate between the Windows® Latin 1 (1250) and Multilingual (850) code pages. The values under the Inventory subkey might be as follows:</para>
    <code>Description : REG_SZ : Inventory database on server InvServ
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL
OEMTOANSI : REG_SZ : Yes
Server : REG_SZ : InvServ
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL
TranslationName : REG_SZ : MS Code Page Translator
TranslationOption : REG_SZ : 12500850</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>