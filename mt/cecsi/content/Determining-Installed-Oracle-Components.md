---
title: Determining Installed Oracle Components
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b018f6a-9db0-4aa1-8ec4-afc5f76d7cad
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Determining Installed Oracle Components
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>To determine the Oracle components installed on your system (and their versions), navigate to the \Orainst directory under the Oracle home directory. Open one of the following text files: Nt.rgs, Win95.rgs, or Win98.rgs.</para>
    <para>The file format is similar to the following:</para>
    <code>0 ntinstall     all    "orainst"  "3.3.1.0.0C"  "Oracle Installer"
20 w32tcp80     adp80  "tcp80"    "8.0.5.0.0"   "Oracle TCP/IP Pro"
23 w32nmp80     adp80  "nmp80"    "8.0.5.0.0"   "Oracle Named Pipe"
26 w32util80    all    "util80"   "8.0.5.0.0"   "Oracle8 Utilities"
34 w32rsf80     all    "rsf80"    "8.0.5.0.0"   "Required Support"
47 w32netclt80  net80  "netc80"   "8.0.5.0.0"   "Oracle Net8 Client"
69 w32plus80    all    "plus80"   "8.0.5.0.0"   "SQL*Plus"</code>
    <para>The .rgs files also include installation information and descriptions of each component.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>