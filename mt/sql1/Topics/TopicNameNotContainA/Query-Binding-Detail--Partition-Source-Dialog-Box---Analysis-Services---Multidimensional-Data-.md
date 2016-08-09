---
title: "Query Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
caps.latest.revision: 22
caps.handback.revision: 0
manager: mblythe
---
# Query Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)
Use the **Query Binding** option in the **Partition Source** dialog box to specify the query that provides the data for the partition. You can display this pane by selecting **Query Binding** from the **Binding type** option in the **Partition Source** dialog box.  
  
## Options  
 **Data source**  
 Select the data source on which the query is executed to provide fact data for the partition.  
  
 **Query**  
 Type or modify the SQL statement used when retrieving fact data when the partition is processed.  
  
> [!IMPORTANT]  
>  By specifying a WHERE clause, a subset of records can be used for this partition. This is essential to prevent duplication of data when multiple partitions are based on a single fact table. For more information, see [Partition Source Dialog Box (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Partition-Source-Dialog-Box--Analysis-Services---Multidimensional-Data-.md).  
  
 **Check**  
 Click to verify that the statement in **Query** is a valid SQL statement.  
  
## See Also  
 [Partition Source Dialog Box (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Partition-Source-Dialog-Box--Analysis-Services---Multidimensional-Data-.md)