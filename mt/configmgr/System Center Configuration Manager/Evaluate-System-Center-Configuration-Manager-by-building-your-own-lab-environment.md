---
title: "Evaluate System Center Configuration Manager by building your own lab environment"
ms.custom: na
ms.date: 2016-06-20
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 01b30260-f03a-4851-a549-d1b76e8cfc69
caps.latest.revision: 25
caps.handback.revision: 0
author: barlanmsft
---
# Evaluate System Center Configuration Manager by building your own lab environment
Learn how to create a lab environment to evaluate System Center Configuration Manager for use in your organization.  
  
## Evaluate System Center Configuration Manager by Building Your Own Lab Environment  
 [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] is a complex and powerful tool to manage your users, devices and software. We recommend you complete a thorough evaluation of [!INCLUDE[cmshortname](../System Center Configuration Manager/itokens/cmshortname_md.md)] prior to full deployment, so that you can marry conceptual understanding with hands-on exercises.  
  
 This guide is primarily intended for administrators evaluating the use of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in corporate environments.  
  
-   Administrators looking for a solution to fully managing PCs, servers and mobile devices  
  
-   Administrators in high-security industries that require the security of on-premise device management with the flexibility of cloud-based device management  
  
-   Administrators looking to manage the scaling-up of their on-premise server architecture  
  
### What this lab does  
 The primary goal of creating this environment is to provide you with the general knowledge to begin working with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], and to enhance your understanding of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] by doing. This is done by walking you through an expedited assembly of the current version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], using two servers:  
  
-   One hosting Active Directory, the Domain Controller, and DNS server  
  
-   A second hosting [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and all associated SQL Server components.  
  
-   Client machines are installed within Hyper-V. The lab itself can also be run as a fully virtualized system on a single server.  
  
### What this lab does not do  
 This lab will not take you through all [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] scenarios, and is not designed to be immediately migrated into an active environment.  
  
 When you build this lab, you will have a functional environment to work in. However, this environment will not be optimized for system performance, hard disk space management, SQL Server storage, etc.  
  
###  <a name="BKMK_EvalRec"></a> Recommended reading prior to beginning the lab  
 There is a wealth of content available in the [Documentation for System Center Configuration Manager](../System Center Configuration Manager/Documentation-for-System-Center-Configuration-Manager.md). A selection of topics from this library have been included below that are recommended for all administrators working on labs to read prior to beginning these exercises.  
  
-   Learn core concepts about the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, end-user portals, and example scenarios in the [Introduction to System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-System-Center-Configuration-Manager.md)  
  
-   Learn about the primary management capabilities of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in [Features and capabilities of System Center Configuration Manager](../System Center Configuration Manager/Features-and-capabilities-of-System-Center-Configuration-Manager.md)  
  
-   Bolster your knowledge with the [Fundamentals of System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-System-Center-Configuration-Manager.md)  
  
-   Learn the importance of security roles in the [Fundamentals of role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-role-based-administration-for-System-Center-Configuration-Manager.md)  
  
-   Understanding these [Concepts for content management](../System Center Configuration Manager/Fundamental-concepts-for-content-management-in-System-Center-Configuration-Manager.md#bkmk_Concepts) can provide you with specific concepts relating to content management  
  
-   [Understand how clients find site resources and services for System Center Configuration Manager](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md) to successfully support daily operations throughout your deployment  
  
## See Also  
 [Set up your System Center Configuration Manager lab](../System Center Configuration Manager/Set-up-your-System-Center-Configuration-Manager-lab.md)