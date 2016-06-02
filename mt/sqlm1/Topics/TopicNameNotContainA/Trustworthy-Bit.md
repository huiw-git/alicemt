---
title: Trustworthy Bit
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
---
# Trustworthy Bit
  This rule determines whether the dbo role for a database is assigned to the sysadmin fixed server role and the database has its trustworthy bit set to ON.  
  
 If these conditions are met, a privileged database user can elevate privileges to the sysadmin role. In this role, the user can create and run unsafe assemblies that compromise the system.  
  
## Best Practices Recommendations  
 Turn off the trustworthy bit or revoke sysadmin permissions from the dbo database role.  
  
## For More Information  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  