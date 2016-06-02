---
title: Place Data and Log Files on Separate Drives
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
---
# Place Data and Log Files on Separate Drives
  This rule checks whether data and log files are placed on separate logical drives. Placing both data AND log files on the same device can cause contention for that device, resulting in poor performance. Placing the files on separate drives allows the I\/O activity to occur at the same time for both the data and log files.  
  
## Recommendations  
 When you create a new database, specify separate drives for the data and logs. To move files after the database is created, the database must be taken offline. Move files by using one of the following methods:  
  
> [!NOTE]  
>  This policy cannot detect separate physical devices through mount points  
  
-   Restore the database from backup by using the RESTORE DATABASE statement with the WITH MOVE option.  
  
-   Detach and then attach the database specifying separate locations for the data and log devices.  
  
-   Specify a new location by running the ALTER DATABASE statement with the MODIFY FILE option, and then restarting the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## For More Information  
 [Move Database Files](../../Topics\TopicNameNotContainA/Move-Database-Files.md)  
  
 [Move User Databases](../../Topics\TopicNameNotContainA/Move-User-Databases.md)  
  
 [Database Detach and Attach &#40;SQL Server&#41;](../Topic/Database%20Detach%20and%20Attach%20\(SQL%20Server\).md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  