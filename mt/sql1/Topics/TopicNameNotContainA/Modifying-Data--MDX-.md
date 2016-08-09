---
title: "Modifying Data (MDX)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: 31
caps.handback.revision: 0
manager: mblythe
---
# Modifying Data (MDX)
Besides using Multidimensional Expressions (MDX) to retrieve and handle data from dimensions and cubes, you can use MDX to update or *writeback* dimension and cube data. These updates can be temporary, as with speculative, or "what if", analysis, or permanent, as when changes must occur based upon data analysis.  
  
 Updates to data can occur at the dimension or cube level:  
  
 **Dimension writebacks**  
 You use the [ALTER CUBE Statement (MDX)](assetId:///2f0af61b-f509-4e1a-990f-20a215d22994) statement to change a write-enabled dimension's data and the [REFRESH CUBE Statement (MDX)](assetId:///b8c087fb-5d17-4b13-b7cf-9929e9aab35c) to reflect the deletion, creation, and updating of attribute values. You can also use the ALTER CUBE statement to perform complex operations, such as deleting a whole sub-tree in a hierarchy and promoting the children of a deleted member.  
  
 **Cube writebacks**  
 You use the [UPDATE CUBE](assetId:///6c8f23bb-401b-49de-843a-5324ac977239) statement to make updates to a write-enabled cube. The UPDATE CUBE statement lets you update a tuple with a specific value. You use the [REFRESH CUBE Statement (MDX)](assetId:///b8c087fb-5d17-4b13-b7cf-9929e9aab35c) to refresh data in a client session with updated data from the server.  
  
 For more information, see [Using Cube Writebacks (MDX)](../../Topics/TopicNameNotContainA/Using-Cube-Writebacks--MDX-.md).  
  
## See Also  
 [MDX Query Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)