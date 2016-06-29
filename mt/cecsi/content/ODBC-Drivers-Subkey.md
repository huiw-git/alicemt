---
title: ODBC Drivers Subkey
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
translation.priority.ht: 
  - en-gb
---
# ODBC Drivers Subkey
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The values under the ODBC Drivers subkey list the installed drivers. The format of these values is shown in the following table.</para>
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
            <para>               <legacyItalic>driver-description</legacyItalic>             </para>
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
    <para>The <legacyItalic>driver-description</legacyItalic> name is defined by the driver developer. It is usually the name of the DBMS associated with the driver.</para>
    <para>For example, suppose drivers have been installed for formatted text files and SQL Server. The values under the ODBC Drivers subkey might be:</para>
    <code>Text : REG_SZ : Installed
SQL Server : REG_SZ : Installed</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>