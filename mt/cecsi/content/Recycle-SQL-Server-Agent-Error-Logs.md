---
title: "Recycle SQL Server Agent Error Logs"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: 3
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
# Recycle SQL Server Agent Error Logs
Use this page to recycle the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent Error Logs. Recycling the log closes the current [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent error log and starts a new error log without restarting the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service. Notice that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent maintains the nine most recent error logs. If there are already nine error logs present, recycling the error log causes [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to remove the oldest error log.  
  
## See Also  
[SQL Server Agent Error Log](../content/SQL-Server-Agent-Error-Log.md)  
  
