---
title: "Building Calculated Members in MDX (MDX)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
caps.latest.revision: 30
caps.handback.revision: 0
manager: mblythe
---
# Building Calculated Members in MDX (MDX)
In Multidimensional Expressions (MDX), a calculated member is a member that is resolved by calculating an MDX expression to return a value. This innocuous definition covers an incredible amount of ground. The ability to construct and use calculated members in an MDX query provides a great deal of manipulation capability for multidimensional data.  
  
 You can create calculated members at any point within a hierarchy. You can also create calculated members that depend not only on existing members in a cube, but also on other calculated members defined in the same MDX expression.  
  
 You can define a calculated member to have one of the following contexts:  
  
-   **Query-scoped** To create a calculated member that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword. You can then use the calculated member within an MDX SELECT statement. Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.  
  
     For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Calculated Members (MDX)](../../Topics/TopicNameNotContainA/Creating-Query-Scoped-Calculated-Members--MDX-.md).  
  
-   **Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE MEMBER statement. A calculated member defined by using the CREATE MEMBER statement is available to all MDX queries in that session. The CREATE MEMBER statement makes sense, for example, in a client application that consistently reuses the same set in a variety of queries.  
  
     For more information about how to use the CREATE MEMBER statement to create calculated members in a session, see [Creating Session-Scoped Calculated Members (MDX)](../../Topics/TopicNameNotContainA/Creating-Session-Scoped-Calculated-Members--MDX-.md).  
  
## See Also  
 [CREATE MEMBER Statement (MDX)](assetId:///49379217-be2c-4139-a206-1168078b9b76)   
 [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d)   
 [SELECT Statement (MDX)](assetId:///c0a57214-aa3f-44ce-a369-660c69746f34)