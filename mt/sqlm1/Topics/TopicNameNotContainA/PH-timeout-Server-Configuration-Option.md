---
title: PH timeout Server Configuration Option
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
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
---
# PH timeout Server Configuration Option
  Use the PH timeout option to specify the time, in seconds, that the full\-text protocol handler should wait to connect to a database before timing out. The default value is 60 seconds. Increase the ph timeout value when connection attempts are timing out due to temporary network issues.  
  
 The full\-text protocol handler is hosted in the filter daemon host and is used to fetch from SQL Server the data to be full\-text indexed. For more information about full\-text search components, see [Full-Text Search](../../Topics\TopicNameNotContainA/Full-Text-Search.md).  
  
 When attempting to fetch a data row, if the protocol handler cannot connect to SQL Server within the specified time, it reports a time\-out error for that row. The full\-text gatherer will retry the row later. For more information about the full\-text gatherer, see [Populate Full-Text Indexes](../../Topics\TopicNameNotContainA/Populate-Full-Text-Indexes.md).  
  
## See Also  
 [Full-Text Search](../../Topics\TopicNameNotContainA/Full-Text-Search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  