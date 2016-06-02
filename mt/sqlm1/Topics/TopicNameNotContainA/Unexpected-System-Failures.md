---
title: Unexpected System Failures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
---
# Unexpected System Failures
  This rule checks for SYSTEM Event 6008 in the computer event log. This event indicates an unexpected system shutdown. The system might be unstable and might not provide the stability and integrity that is required to host an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## Best Practices Recommendations  
 Immediately address the cause of the unexpected server restarts, or move the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to another computer.  
  
  