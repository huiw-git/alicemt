---
title: "Set the PAGE_VERIFY Database Option to CHECKSUM"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Set the PAGE_VERIFY Database Option to CHECKSUM
This rule checks whether PAGE_VERIFY database option is set to CHECKSUM. When CHECKSUM is enabled for the PAGE_VERIFY database option, the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] calculates a checksum over the contents of the whole page, and stores the value in the page header when a page is written to disk. When the page is read from disk, the checksum is recomputed and compared to the checksum value that is stored in the page header. This helps provide a high level of data-file integrity.  
  
## Best Practices Recommendations  
 Set the PAGE_VERIFY database option to CHECKSUM.  
  
## For More Information  
 [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc)