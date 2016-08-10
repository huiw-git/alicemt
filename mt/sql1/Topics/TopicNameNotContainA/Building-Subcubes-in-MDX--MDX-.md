---
title: "Building Subcubes in MDX (MDX)"
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
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
caps.latest.revision: 32
caps.handback.revision: 0
manager: mblythe
---
# Building Subcubes in MDX (MDX)
A subcube is a subset of a cube on representing a filtered view of the underlying data. By limiting the cube to a subcube, you can improve query performance.  
  
 To define a subcube, you use the [CREATE SUBCUBE](assetId:///15b6ac4c-b68a-4f9f-b33c-f5f7c4a74535) statement, as described in this topic.  
  
## CREATE SUBCUBE Syntax  
 Use the following syntax to create a subcube:  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 The CREATE SUBCUBE syntax is fairly simple. The *Subcube_Identifier* parameter identifies the cube on which the subcube will be based. The *Subcube_Expression* parameter selects the part of the cube that will become the subcube  
  
 After you create a subcube, that subcube becomes the context for all MDX queries until either the session closes or you run the [DROP SUBCUBE](assetId:///d8771b38-7a8f-40b2-947f-dd6d47e89ae3) statement.  
  
### What a Subcube Contains  
 Although the CREATE SUBCUBE statement is fairly simple to use, the statement itself does not explicitly show all the members that become part of a subcube. In defining a subcube, the following rules apply:  
  
-   If you include the **(All)** member of a hierarchy, you include every member of that hierarchy.  
  
-   If you include any member, you include that member's ascendants and descendants.  
  
-   If you include every member from a level, you include all members from the hierarchy. Members from other hierarchies will be excluded if those members do not exist with members from the level (for example, an unbalanced hierarchy such as a city that does not contain customers).  
  
-   A subcube will always contain every **(All)** member from the cube.  
  
 Additionally, aggregate values within the subcube are visually totaled. For example, a subcube contains `USA`, `WA`, and `OR`. The aggregate value for `USA` will be the sum of `{WA,OR}` because `WA` and `OR` are the only states defined by the subcube. All other states will be ignored.  
  
 Also, explicit references to cells outside the subcube return cell values that are evaluated in the context of the whole cube. For example, you create a subcube that is limited to the current year. You then use the [ParallelPeriod](assetId:///9c87f5a6-5694-46f1-9890-bd9705190ea7) function to compare the current year to the previous year. The difference in values will be returned even though the previous year’s value lies outside the subcube.  
  
 Finally, if the original context is not overwritten, set functions evaluated in a subselect are evaluated in the context of the subselect. If the context is overwritten, set functions are evaluated in the context of the whole cube.  
  
## CREATE SUBCUBE Example  
 The following example creates a subcube that restricts the Budget cube to only accounts 4200 and 4300:  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 Having created a subcube for the session, any subsequent queries will be against the subcube, not the whole cube. For example, you run the following query. This query will only return members from accounts 4200 and 4300.  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## See Also  
 [Establishing Cube Context in a Query (MDX)](../../Topics/TopicNameContainA/Establishing-Cube-Context-in-a-Query--MDX-.md)   
 [MDX Query Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)