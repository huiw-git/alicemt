---
title: "Release Notes for the Microsoft ODBC Driver for SQL Server on Linux"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 905b595b-9aac-4e6a-8ed1-3a5ed96077d8
caps.latest.revision: 6
manager: jhubbard
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
# Release Notes for the Microsoft ODBC Driver for SQL Server on Linux
Release Notes for Microsoft ODBC Driver for SQL Server on Linux.  
  
## What's New in the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] ODBC Driver 13 (Preview) for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] on Linux  
With Microsoft ODBC Driver 13 (Preview) for SQL Server, SQL Server 2014 and SQL Server 2016 (Preview), are now also supported.  
  
**Always Encrypted**  
  
Support for the recently released Always Encrypted feature in SQL Server 2016 (Preview), a new security feature that ensures sensitive data is never seen in plaintext in a SQL Server instance. Always Encrypted works by transparently encrypting the data in the application, so that SQL Server will only handle the encrypted data and not plaintext values. Even if the SQL instance or the host machine is compromised, all an attacker can get is ciphertext of sensitive data.. For details see [Using Always Encrypted with the Linux ODBC Driver](../content/Using-Always-Encrypted-with-the-Linux-ODBC-Driver.md).  
  
**Ubuntu Support**  
  
Ubuntu is now supported, along with Red Hat and SUSE. You can download for Ubuntu here: [Microsoft ODBC Driver 13 (Preview) for SQL Server - Ubuntu Linux](http://go.microsoft.com/fwlink/?LinkId=??).  
  
**unixODBC Driver Manager 2.3.1 Support**  
  
For details on Driver Manager Support see [Installing the Driver Manager](../content/Installing-the-Driver-Manager.md).  
  
## What's New in the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] on Linux  
The ODBC driver on SUSE Linux (Preview) supports 64-bit SUSE Linux Enterprise 11 Service Pack 2. For more information, see [System Requirements](../content/System-Requirements.md).  
  
The ODBC driver on Linux supports [!INCLUDE[ssHADR](../content/includes/ssHADR_md.md)]. For more information, see [ODBC Driver on Linux Support for High Availability, Disaster Recovery](../content/ODBC-Driver-on-Linux-Support-for-High-Availability--Disaster-Recovery.md).  
  
The ODBC driver on Linux supports connections to Microsoft Azure SQL Database. For more information, see [How to: Connect to Windows Azure SQL Database Using ODBC](http://msdn.microsoft.com/library/hh974312.aspx).  
  
The driver supports tracing of ODBC API call entry and exit. For more information, see [Data Access Tracing with the ODBC Driver on Linux](../content/Data-Access-Tracing-with-the-ODBC-Driver-on-Linux.md).  
  
The **-l** option has been added to bcp. For more information, see [Connecting with bcp](../content/Connecting-with-bcp.md).  
  
