---
title: "Creating Session-Scoped Calculated Cells"
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
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
caps.latest.revision: 15
caps.handback.revision: 0
manager: mblythe
---
# Creating Session-Scoped Calculated Cells
> [!IMPORTANT]  
>  This syntax has been deprecated. You should use MDX assignments should instead. For more information on assignments, see [The Basic MDX Script (MDX)](../../Topics/TopicNameNotContainA/The-Basic-MDX-Script--MDX-.md).  
  
 To create calculated cells that are available to all queries in the same session, you can use either the [CREATE CELL CALCULATION](assetId:///01ced1b3-ada1-4b55-b350-e4255c3cc679) statement or the [ALTER CUBE](assetId:///2f0af61b-f509-4e1a-990f-20a215d22994) statement. Both statements have the same result.  
  
## CREATE CELL CALCULATION Syntax  
  
> [!IMPORTANT]  
>  This syntax has been deprecated. You should use MDX assignments should instead. For more information on assignments, see [The Basic MDX Script (MDX)](../../Topics/TopicNameNotContainA/The-Basic-MDX-Script--MDX-.md).  
  
 Use the following syntax to use the CREATE CELL CALCULATION statement to define a session-scoped calculated cell:  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## ALTER CUBE Syntax  
  
> [!IMPORTANT]  
>  This syntax has been deprecated. You should use MDX assignments should instead. For more information on assignments, see [The Basic MDX Script (MDX)](../../Topics/TopicNameNotContainA/The-Basic-MDX-Script--MDX-.md).  
  
 Use the following syntax to use the ALTER CUBE statement to define a session-scoped calculated cell:  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions, each of which must resolve to one of the categories of sets that are listed in the following table.  
  
|Category|Description|  
|--------------|-----------------|  
|Empty set|An MDX set expression that resolves into an empty set. In this case, the scope of the calculated cell is the whole cube.|  
|Single member set|An MDX set expression that resolves into a single member.|  
|Set of level members|An MDX set expression that resolves into the members of a single level. An example of this is the *Level_Expression*.**Members** MDX function. To include calculated members, use the *Level_Expression*.**AllMembers** MDX function.<br /><br /> For more information, see [AllMembers (MDX)](assetId:///202e81d4-d2ee-4ec1-a019-4835eb19f446).|  
|Set of descendants|An MDX set expression that resolves into the descendants of a specified member. An example of this is the **Descendants**(*Member_Expression*, *Level_Expression*, *Desc_Flag*) MDX function.<br /><br /> For more information, see [Descendants (MDX)](assetId:///d103b0f5-e794-4828-aa57-43f6918a0749).|  
  
## See Also  
 [Building Cell Calculations in MDX (MDX)](../../Topics/TopicNameNotContainA/Building-Cell-Calculations-in-MDX--MDX-.md)