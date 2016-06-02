---
title: Install SQL Server 2016 Servicing Updates
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
---
# Install SQL Server 2016 Servicing Updates
  This topic provides information about installing updates for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. This section provides information about the following:  
  
-   Installing updates for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] during a new installation  
  
-   Installing updates for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] after it has already been installed.  
  
 We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] updates in a timely manner to make sure that systems are up\-to\-date with the most recent security updates.  
  
## Installing Updates for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] During a New Installation  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time. Product Update can search for the applicable updates from:  
  
-   [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Update  
  
-   Windows Server Update Services \(WSUS\)  
  
-   A local folder  
  
-   A network share  
  
 After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup process. Product Update can include a cumulative update, service pack, or service pack plus cumulative update.  
  
## Installing Updates for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] after it has already been installed  
 On an installed instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], we recommend that you apply the latest security updates and critical updates including General Distribution Releases \(GDRs\), and Service Packs \(SPs\). Individual Cumulative updates and security updates should be adopted on a case\-by\-case, "as\-needed" basis.  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] updates are available through [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Update \(MU\), Windows Server Update Services \(WSUS\) and the Microsoft Download Center. Security and Critical updates for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] are available through [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Update, and to be able to see these updates you need to opt\-into MU through the Windows Update applet in Control panel.  
  
 When you receive an update through [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Update, it will update all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features to the latest version in an unattended mode. If you need more flexibility or don’t have internet or WSUS access you will need to obtain the updates from the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Download Center.  
  
## See Also  
 [Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md)   
 [Add Features to an Instance of SQL Server 2016 &#40;Setup&#41;](../Topic/Add%20Features%20to%20an%20Instance%20of%20SQL%20Server%202016%20\(Setup\).md)   
 [Repair a Failed SQL Server 2016 Installation](../../Topics\TopicNameContainA/Repair-a-Failed-SQL-Server-2016-Installation.md)  
  
  