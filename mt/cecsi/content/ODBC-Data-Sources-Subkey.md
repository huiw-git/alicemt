---
title: ODBC Data Sources Subkey
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Data Sources Subkey
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The values under the ODBC Data Sources subkey list the data sources. The format of these values is as shown in the following table.</para>
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
            <para>               <legacyItalic>data-source-name</legacyItalic>             </para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyItalic>driver-description</legacyItalic>             </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The <legacyItalic>data-source-name</legacyItalic> value is defined by the administration program (which usually prompts the user for it), and <legacyItalic>driver-description</legacyItalic> is defined by the driver developer (it is usually the name of the DBMS associated with the driver).</para>
    <para>For example, suppose three data sources have been defined: Inventory, which uses SQL Server; Payroll, which uses dBASE; and Personnel, which uses formatted text files. The values under the ODBC Data Sources subkey might be as follows:</para>
    <code>Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>