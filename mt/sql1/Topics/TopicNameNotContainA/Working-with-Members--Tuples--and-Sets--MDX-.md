---
title: "Working with Members, Tuples, and Sets (MDX)"
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
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
caps.latest.revision: 42
caps.handback.revision: 0
manager: mblythe
---
# Working with Members, Tuples, and Sets (MDX)
MDX provides numerous functions that return one or more members, tuples, or sets; or that act upon a member, tuple, or set.  
  
## Member Functions  
 MDX provides several functions for retrieving members from other MDX entities, such as from dimensions, levels, sets, or tuples. For example, the [FirstChild](assetId:///3c19a169-7658-4b31-93a9-85f74225ba05) function is a function that acts upon a member and returns a member.  
  
 To obtain the first child member of the Time dimension, you can explicitly state the member, as in the following example.  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 You can also use the **FirstChild** function to return the same member, as in the following example.  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 For more information about MDX member functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## Tuple Functions  
 MDX provides several functions that return tuples, and they can be used anywhere that a tuple is accepted. For example, the [Item (Tuple) (MDX)](assetId:///9ee7af55-d5b5-47c8-a480-ef23878306af) function can be used to extract the first tuple from set, which is very useful when you know that a set is composed of a single tuple and you want to supply that tuple to a function that requires a tuple.  
  
 The following example returns the first tuple from within the set of tuples on the column axis.  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 For more information about tuple functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## Set Functions  
 MDX provides several functions that return sets. Explicitly typing tuples and enclosing them in braces is not the only way to retrieve a set. For more information about the members function to return a set, see [Key Concepts in MDX (Analysis Services)](../../Topics/TopicNameNotContainA/Key-Concepts-in-MDX--Analysis-Services-.md). There are many additional set functions.  
  
 The colon operator lets you use the natural order of members to create a set. For example, the set shown in the following example contains tuples for the 1st through the 4th quarter of calendar year 2002.  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 If you do not use the colon operator to create the set, you can create the same set of members by specifying the tuples in the following example.  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 The colon operator is an inclusive function. The members on both sides of the colon operator are included in the resulting set.  
  
 For more information about set functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## Array Functions  
 An array function acts upon a set and returns an array. For more information about array functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## Hierarchy Functions  
 A hierarchy function returns a hierarchy by acting upon a member, level, hierarchy, or string. For more information about hierarchy functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## Level Functions  
 A level function returns a level by acting upon a member, level, or string. For more information about level functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## Logical Functions  
 A logical function acts upon a MDX expression to return information about the tuples, members, or sets in the expression. For example, the [IsEmpty (MDX)](assetId:///b4a50996-61d1-4e23-8003-7d530195ea72) function evaluates whether an expression has returned an empty cell value. For more information about logical functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## Numeric Functions  
 A numeric function acts upon a MDX expression to return a scalar value. For example, the [Aggregate (MDX)](assetId:///9d5e0966-74d1-4cc8-b9f9-47e4dc65d165) function returns a scalar value calculated by aggregating measures over the tuples in a specified set. For more information about numeric functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## String Functions  
 A string function acts upon a MDX expression to return a string. For example, the [UniqueName (MDX)](assetId:///f186094e-670c-401c-a82f-6b634b3f71f5) function returns a string value containing the unique name of a dimension, hierarchy, level, or member. For more information about string functions, see [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d).  
  
## See Also  
 [Key Concepts in MDX (Analysis Services)](../../Topics/TopicNameNotContainA/Key-Concepts-in-MDX--Analysis-Services-.md)   
 [MDX Query Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)   
 [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d)