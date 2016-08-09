---
title: "Prepare Image Rules"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 609a7c06-9527-4ef5-8e75-0c44e1958c5a
caps.latest.revision: 17
caps.handback.revision: 0
manager: jhubbard
---
# Prepare Image Rules
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup validates your computer configuration before the Setup operation completes. During [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] will be installed. The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup operation. Before Setup starts the wizard, the SCC retrieves the status of each item. It then compares the result with required conditions and provides guidance for removal of blocking issues.  
  
 The system configuration check generates a report which contains a short description for each executed rule, and the execution status. The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]\130\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.  
  
 Before you run the setup operation, review the following topics:  
  
1.  [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics/TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md)  
  
2.  [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)  
  
3.  [Security Considerations for a SQL Server Installation](../../Topics/TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)  
  
4.  [Local Language Versions in SQL Server](../../Topics/TopicNameNotContainA/Local-Language-Versions-in-SQL-Server.md)  
  
 Other references:  
  
1.  [Supported Version and Edition Upgrades](../../Topics/TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md)  
  
2.  [Before Installing Failover Clustering](../../Topics/TopicNameNotContainA/Before-Installing-Failover-Clustering.md)