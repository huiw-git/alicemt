---
title: Backup Files Must Be on Separate Devices from the Database Files
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
---
# Backup Files Must Be on Separate Devices from the Database Files
  This rule checks whether database files are on devices separate from the backup files. If database files and backup files are on the same device and the device fails, the database and backups will be unavailable. Also, putting the database and backup files on the separate devices optimizes the I\/O performance for both the production use of the database and the writing of backups.  
  
## Best Practices Recommendations  
 We strongly recommend that you put the database and backups on separate backup devices.  
  
> [!NOTE]  
>  This policy cannot detect separate physical devices through mount points.  
  
## For More Information  
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)  
  
 [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  