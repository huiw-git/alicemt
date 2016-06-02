---
title: PolyBase FAQ
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-polybase
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 197fa2ce-9ee2-495f-abd3-79fea5dbe326
---
# PolyBase FAQ
  Q: Does PolyBase work against HDInsight?  
 No, currently PolyBase does not work against HDI. See [PolyBase Connectivity Configuration &#40;Transact-SQL&#41;](../Topic/PolyBase%20Connectivity%20Configuration%20\(Transact-SQL\).md) for the list of connectivity options.  
  
 Q:  Does PolyBase work against Azure Data Lake Store?  
 No, currently PolyBase does not work against Data Lake Store.  
  
 Q: Can I reference hive tables in the external table?  
 No, you have to reference the HDFS data.  
  
 Q: Can I reference an external table from a view?  
 Yes. You can use external tables as if they are local tables.  
  
 Q: Can computation be pushed down to Azure storage blobs?  
 No, since there is no computation engine on blob storage, computation cannot be pushed to the data.  
  
  