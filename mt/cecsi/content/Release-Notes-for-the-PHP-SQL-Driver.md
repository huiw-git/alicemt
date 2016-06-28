---
title: Release Notes for the PHP SQL Driver
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Release Notes for the PHP SQL Driver
This topic discusses what was added in the 3.2, 3.1, 3.0, and 2.0 versions of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## What's New in Version 3.2  
Support for PHP 5.6  
  
Includes latest updates for prior PHP versions 5.5 and 5.4  
  
Requires Microsoft ODBC Driver 11 \(or higher\) for SQL Server  
  
## What's New in Version 3.1  
Support for PHP 5.5  
  
Requires Microsoft ODBC Driver 11 \(or higher\) for SQL Server. Previous versions required SQL Native Client.  
  
## What's New in Version 3.0  
Support for PHP 5.4.  PHP 5.2 is not supported in version 3 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
AttachDBFileName connection option is added. For more information, see [Connection Options](../content/Connection-Options.md).  
  
Support for LocalDB, which was added in [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)]. For more information, see [PHP Driver for SQL Server Support for LocalDB](../content/PHP-Driver-for-SQL-Server-Support-for-LocalDB.md).  
  
AttachDBFileName connection option is added. For more information, see [Connection Options](../content/Connection-Options.md).  
  
Support for the high\-availability, disaster recovery features. For more information, see [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../content/PHP-Driver-for-SQL-Server-Support-for-High-Availability--Disaster-Recovery.md).  
  
Support for client\-side cursors \(caching a result set in\-memory\). For more information, see [Cursor Types &#40;SQLSRV Driver&#41;](../content/Cursor-Types--SQLSRV-Driver-.md) and [Cursor Types &#40;PDO_SQLSRV Driver&#41;](../content/Cursor-Types--PDO_SQLSRV-Driver-.md).  
  
The PDO::ATTR\_EMULATE\_PREPARES attribute has been added.  See [PDO::prepare](../Topic/PDO::prepare.md) for more information.  
  
## What's New in Version 2.0  
In version 2.0, support for the PDO\_SQLSRV driver was added. For more information, see [PDO_SQLSRV Driver Reference](../content/PDO_SQLSRV-Driver-Reference.md).  
  
## See Also  
[Overview of the PHP SQL Driver](../content/Overview-of-the-PHP-SQL-Driver.md)
  
