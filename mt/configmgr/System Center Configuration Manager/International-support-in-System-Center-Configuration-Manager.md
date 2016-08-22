---
title: "International support in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 46dd9cb2-a812-4b6a-a747-b840f92fef8b
caps.latest.revision: 6
caps.handback.revision: 0
---
# International support in System Center Configuration Manager
The following sections provide technical details to help you configure [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to be compliant for specific international requirements.  
  
## GB18030 Requirements  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] meets the standards that are defined in GB18030 so that you can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in China. A [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] deployment must have the following configurations to meet the GB18030 requirements:  
  
-   Each site server computer and SQL Server computer that you use with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] must use a Chinese operating system.  
  
-   Each site database and each instance of SQL Server in the hierarchy must use the same collation, and must be one of the following:  
  
    -   Chinese_Simplified_Pinyin_100_CI_AI  
  
    -   Chinese_Simplified_Stroke_Order_100_CI_AI  
  
    > [!NOTE]  
    >  These database collations are an exception to the requirements noted in [Support for SQL Server versions for System Center Configuration Manager](../System Center Configuration Manager/Support-for-SQL-Server-versions-for-System-Center-Configuration-Manager.md).  
  
-   You must place a file with the name **GB18030.SMS** in the root folder of the system volume of each site server computer in the hierarchy. This file does not contain any data and can be an empty text file that is named to meet this requirement.  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)