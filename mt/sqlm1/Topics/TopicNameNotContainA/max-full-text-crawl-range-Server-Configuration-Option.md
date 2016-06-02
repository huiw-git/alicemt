---
title: max full-text crawl range Server Configuration Option
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
---
# max full-text crawl range Server Configuration Option
  Use the **max full\-text crawl range** option to optimize CPU utilization, which improves crawl performance during a full crawl. Using this option, you can specify the number of partitions that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] should use during a full index crawl. For example, if there are many CPUs and their utilization is not optimal, you can increase the maximum value of this option. In addition to this option, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses a number of other factors, such as the number of rows in the table and the number of CPUs, to determine the actual number of partitions used.  
  
 The default value of this option is 4; the minimum value is 1, and the maximum value is 256. Changes made to this option affect only subsequent crawls. Crawls in process will not be affected by a change in this option setting.  
  
 The **max full\-text crawl range** option is an advanced option. If you are using the **sp\_configure** system stored procedure to change the setting, you can change **max full\-text crawl range** only when **show advanced options** is set to 1. The setting takes effect immediately without a server restart.  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  