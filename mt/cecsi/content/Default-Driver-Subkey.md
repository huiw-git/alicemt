---
title: Default Driver Subkey
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Default Driver Subkey
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Default subkey contains a single value that describes the driver used by the default data source. The format of this value is shown in the following table.</para>
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
            <para>               <legacyBold>Driver</legacyBold>             </para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>               <legacyItalic>default-driver-description</legacyItalic>             </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The <legacyItalic>default-driver-description</legacyItalic> name is the same as the name of the value under the ODBC Drivers subkey that describes the driver.</para>
    <para>For example, if the default data source uses the SQL Server driver, the value under the Default subkey might be:</para>
    <code>Driver : REG_SZ : SQL Server</code>
    <alert class="note">
      <para>The default driver contained in the Default subkey can refer to either a default user DSN or a default system DSN. If both a default user DSN and a default system DSN have been created, the default driver is determined by the DSN that was created last, so it might not be a valid entry for the DSN that was created first.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>