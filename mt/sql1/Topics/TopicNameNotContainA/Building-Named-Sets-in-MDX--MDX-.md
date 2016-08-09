---
title: "Building Named Sets in MDX (MDX)"
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
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
caps.latest.revision: 29
manager: mblythe
---
# Building Named Sets in MDX (MDX)
A set expression can be a lengthy and complex declaration, and therefore be difficult to follow or understand. Or, a set expression may be used so frequently that repeatedly defining the set becomes burdensome. To help make working with a lengthy, complex or commonly used expression easier, Multidimensional Expressions (MDX) lets you such an expression as a *named set*.  
  
 Basically, a named set is a set expression to which an alias has been assigned. A named set can incorporate any members or functions that can ordinarily be incorporated into a set. Because MDX treats the named set alias as a set expression, you can use that alias anywhere a set expression is accepted.  
  
 You can define a named set to have one of the following contexts:  
  
-   **Query-scoped** To create a named set that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword. You can then use the named set within an MDX SELECT statement. Using this approach, the named set created by using the WITH keyword can be changed without disturbing the SELECT statement.  
  
     For more information about how to use the WITH keyword to create named sets, see [Creating Query-Scoped Named Sets (MDX)](../../Topics/TopicNameNotContainA/Creating-Query-Scoped-Named-Sets--MDX-.md).  
  
-   **Session-scoped** To create a named set whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE SET statement. A named set defined by using the CREATE SET statement is available to all MDX queries in that session. The CREATE SET statement makes sense, for example, in a client application that consistently reuses a set in a variety of queries.  
  
     For more information about how to use the CREATE SET statement to create named sets in a session, see [Creating Session-Scoped Named Sets (MDX)](../../Topics/TopicNameNotContainA/Creating-Session-Scoped-Named-Sets--MDX-.md).  
  
## See Also  
 [SELECT Statement (MDX)](assetId:///c0a57214-aa3f-44ce-a369-660c69746f34)   
 [CREATE SET Statement (MDX)](assetId:///eff51eeb-5e7e-4706-b861-c57b6f3f89f0)   
 [MDX Query Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)