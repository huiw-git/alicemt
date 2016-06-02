---
title: Set the PAGE_VERIFY Database Option to CHECKSUM
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
---
# Set the PAGE_VERIFY Database Option to CHECKSUM
  This rule checks whether PAGE\_VERIFY database option is set to CHECKSUM. When CHECKSUM is enabled for the PAGE\_VERIFY database option, the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] calculates a checksum over the contents of the whole page, and stores the value in the page header when a page is written to disk. When the page is read from disk, the checksum is recomputed and compared to the checksum value that is stored in the page header. This helps provide a high level of data\-file integrity.  
  
## Best Practices Recommendations  
 Set the PAGE\_VERIFY database option to CHECKSUM.  
  
## For More Information  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)  
  
  