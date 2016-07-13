---
title: SQL Server Agent Properties (History Page)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
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
# SQL Server Agent Properties (History Page)
Use this page to view and modify settings for managing the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service history log.  
  
## Options  
**Limit size of job history log**  
Sets limits for the amount of job history information that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent retains in the log.  
  
**Maximum job history log size (in rows)**  
Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent retains. When the log grows to contain this number of rows, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent removes the oldest rows in the log as new rows are entered.  
  
**Maximum job history rows per job**  
Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent retains per job. When the history for a particular job grows to contain this number of rows, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent removes the oldest rows in the log as new rows are entered.  
  
**Remove agent history**  
Specifies that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent will remove entries that have been in the log longer than a specified length of time. This is a one\-time execution to remove the history. If a reoccurring job is needed, create and schedule a maintenance plan with a cleanup job.  
  
**Older than**  
Sets the amount of time that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent will retain entries.  
  
## See Also  
[SQL Server Agent Error Log](../content/SQL-Server-Agent-Error-Log.md)  
  
