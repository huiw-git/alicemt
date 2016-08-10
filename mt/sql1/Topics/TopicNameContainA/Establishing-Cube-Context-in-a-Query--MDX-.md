---
title: "Establishing Cube Context in a Query (MDX)"
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
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
caps.latest.revision: 30
caps.handback.revision: 0
manager: mblythe
---
# Establishing Cube Context in a Query (MDX)
Every MDX query runs within a specified cube context. This context defines the members that are evaluated by the expressions within the query.  
  
 In the SELECT statement, the FROM clause determines the cube context. This context can be the whole cube or just a subcube from that cube. Having specified cube context through the FROM clause, you can use additional functions to expand or restrict that context.  
  
> [!NOTE]  
>  The SCOPE and CALCULATE statements also let you manage cube context from within an MDX script. For more information, see [MDX Scripting Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Scripting-Fundamentals--Analysis-Services-.md).  
  
## FROM Clause Syntax  
 The following syntax describes the FROM clause:  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 In this syntax, notice that it is the `<SELECT subcube clause>` clause that describes the cube or subcube on which the SELECT statement is executed.  
  
 A simple example of a FROM clause would be one that runs against the entire Adventure Works sample cube. Such a FROM clause would have the following format:  
  
```  
FROM [Adventure Works]  
```  
  
 For more information about the FROM clause in the MDX SELECT statement, see [SELECT Statement (MDX)](assetId:///c0a57214-aa3f-44ce-a369-660c69746f34).  
  
## Refining the Context  
 Although the FROM clause specifies the cube context as within a single cube, this does not have to limit you from working with data from more than one cube at a time.  
  
 You can use the MDX [LookupCube](assetId:///243fa101-328a-4016-86e0-d8b5977e15a9) function to retrieve data from cubes outside the cube context. Additionally, functions such as the [Filter](assetId:///f2df51c8-6acb-4300-b71c-2a480c9fbdf8) function, are available that allow temporary restriction of the context while evaluating the query.  
  
## See Also  
 [MDX Query Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)