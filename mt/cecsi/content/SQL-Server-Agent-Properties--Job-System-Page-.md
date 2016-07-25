---
title: "SQL Server Agent Properties (Job System Page)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
caps.latest.revision: 4
manager: jhubbard
translation.priority.mt: 
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
# SQL Server Agent Properties (Job System Page)
Use this page to view and modify how the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent Service manages jobs.  
  
## Options  
**Shutdown time-out interval (in seconds)**  
Specifies the number of seconds that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent waits for jobs to complete before shutting down. If the job is still running after the interval specified, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent forcefully stops the job.  
  
**Use a non-administrator proxy account**  
Sets a non-administrator proxy account for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent. [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssKatmai](../content/includes/ssKatmai_md.md)] and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../content/includes/ssKatmai_md.md)].  
  
**User name**  
Type the name of the user for the non-administrator proxy account. [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../content/includes/ssKatmai_md.md)].  
  
**Password**  
Type the password of the user for the non-administrator proxy account. [!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)] and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent versions prior to [!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)].  
  
**Domain**  
Type the domain of the user for the non-administrative proxy account. [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../content/includes/ssKatmai_md.md)].  
  
## See Also  
[Implement Jobs](../content/Implement-Jobs.md)  
  
