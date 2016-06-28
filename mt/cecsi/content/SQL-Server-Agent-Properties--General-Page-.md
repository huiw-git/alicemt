---
title: SQL Server Agent Properties (General Page)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
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
# SQL Server Agent Properties (General Page)
Use this page to view and modify the general properties of the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service.  
  
## Options  
**Service state**  
Displays the current state of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service.  
  
**Auto restart SQL Server if it stops unexpectedly**  
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent restarts [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] if [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] stops unexpectedly.  
  
**Auto restart SQL Server Agent if it stops unexpectedly**  
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] restarts [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent if [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent stops unexpectedly.  
  
**Filename**  
Specify the file name for the error log.  
  
**...**  
Browse to the error log file.  
  
**Include execution trace messages**  
Includes execution trace messages in the error log. Trace messages provide detailed information on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent operation. Therefore, the log file requires more disk space when this option is selected. This option should only be selected while troubleshooting a problem that may involve [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent.  
  
**Write OEM file**  
Writes the error log file as a non\-Unicode file. This reduces the amount of disk space consumed by the log file. However, messages that include Unicode data may be more difficult to read when this option is enabled.  
  
**Net send recipient**  
Type the name of an operator to receive net send notification of messages that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent writes to the log file.  
  
## See Also  
[Operators](../content/Operators.md)  
[SQL Server Agent Error Log](../content/SQL-Server-Agent-Error-Log.md)  
  
