---
title: Check Parameters for the System Configuration Checker
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
---
# Check Parameters for the System Configuration Checker
  During [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup, the System Configuration Checker \(SCC\) scans the computer where [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will be installed. The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation. Before Setup starts the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard, the SCC retrieves the status of each item. It then compares the result with required conditions and provides guidance for removal of blocking issues.  
  
 The system configuration checker generates a report which contains a short description for each executed rule, and the execution status. The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## See Also  
 [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md)   
 [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)   
 [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md)  
  
  