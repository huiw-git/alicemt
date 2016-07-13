---
title: Testing the ODBC Connection
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Testing the ODBC Connection
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>When troubleshooting ODBC access to Oracle 7.x and Oracle8 RDBMS servers, it might be necessary to verify that the underlying SQL*Net and Oracle Protocol Adapters are correctly installed. To do this, use the Oracle-supplied utility Nettest.exe in the Orawin\Bin directory.</para>
    <para>Nettest is a simple utility that attempts to log on to the selected server using only the installed SQL*Net software that is part of the Oracle client. The utility will ask for a login name, password, and TNS connect string. If the Oracle client is correctly installed, the utility will simply display "Ping Successful." If the login was not successful, you will need to consult with a database administrator.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>