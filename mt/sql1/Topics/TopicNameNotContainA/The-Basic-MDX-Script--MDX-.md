---
title: "The Basic MDX Script (MDX)"
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
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
caps.latest.revision: 28
caps.handback.revision: 0
manager: mblythe
---
# The Basic MDX Script (MDX)
A Multidimensional Expressions (MDX) script defines the calculation process for a cube in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]. There are two types of MDX scripts:  
  
 **The default MDX script**  
 At the time that you create a cube, [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] creates a default MDX script for that cube. This script defines a calculation pass for the whole cube.  
  
 **User-defined MDX script**  
 After you have created a cube, you can add user-defined MDX scripts that extend the calculation capabilities of the cube.  
  
## The Default MDX Script  
 The default MDX script that [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] creates when you define a cube contains a single CALCULATE statement. This single CALCULATE statement is at the beginning of the default MDX script, and indicates that the entire cube should be calculated during the first calculation pass.  
  
 The default MDX script also contains the script commands that create named sets, assignments, and calculated members created in Cube Designer:  
  
-   [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] directly adds script commands to the default MDX script.  
  
-   For each named set in the cube, a corresponding CREATE SET statement exists in the default MDX script.  
  
-   For each calculated member defined in the cube, a corresponding CREATE MEMBER statement exists in the default MDX script.  
  
 You can control the order of script commands, named sets, and calculated members in the default MDX script by using the **Calculations** tab of Cube Designer. For more information on defining calculations stored in the default MDX script, see [Calculations in Multidimensional Models](../../Topics/TopicNameNotContainA/Calculations-in-Multidimensional-Models.md).  
  
 If there is no MDX script associated with a cube, the cube assumes the default MDX script. A cube needs to be associated with at least one MDX script because a cube relies on the MDX script to determine calculation behavior. In other words, a cube that was not associated with an MDX script or was associated with an empty MDX script could not and would not be able to calculate any cells. If you programmatically create cubes, either by using Analysis Services Scripting Language (ASSL) commands or by using Analysis Management Objects (AMO), it is recommended that you create a default MDX script containing a single CALCULATE statement for the cube.  
  
## MDX Script Content  
 An MDX script can contain the following statements and expressions:  
  
 All MDX scripting statements  
 In MDX scripts, MDX scripting statements control the context and scope of calculations, and manage the behavior of other statements in the MDX script. This category includes the following statements:  
  
-   [CALCULATE](assetId:///41e196a1-d49e-487b-a42a-73e5d441ed1b)  
  
-   [FREEZE](assetId:///59f1e860-6f37-41af-97d6-7708bdaac933)  
  
-   [SCOPE](assetId:///ceab459d-b601-4468-b3fc-4f5bb4a1805f)  
  
 For more information on MDX scripting statements, see [MDX Scripting Statements (MDX)](assetId:///a4e5f377-6f06-4888-9663-91105b205ac1).  
  
 [CREATE MEMBER](assetId:///49379217-be2c-4139-a206-1168078b9b76)  
 The CREATE MEMBER statement creates calculated members. For more information about how to create calculated members, see [Building Calculated Members in MDX (MDX)](../../Topics/TopicNameNotContainA/Building-Calculated-Members-in-MDX--MDX-.md).  
  
 [CREATE SET](assetId:///eff51eeb-5e7e-4706-b861-c57b6f3f89f0)  
 The CREATE SET statement creates named sets. For more information about how to create names sets, see [Building Named Sets in MDX (MDX)](../../Topics/TopicNameNotContainA/Building-Named-Sets-in-MDX--MDX-.md).  
  
 Conditional statements  
 Conditional statements add conditional logic to MDX scripts. This category includes the [CASE](assetId:///0aee3b4a-d5f7-4c9a-87b8-e5efc2da6b6d) and [IF](assetId:///8830cce5-9e06-4f89-a555-295bb0d0a8a1) statements.  
  
 Assignment expressions  
 An assignment expression assigns an expression, such as a value, to a constrained subcube. A constrained subcube expression is a collection of constrained set expressions that define the "edges" of a subcube within an MDX script. The following codes shows the syntax for a constrained subcube expression:  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## See Also  
 [MDX Language Reference (MDX)](assetId:///8ceaedd3-7679-4300-83a5-4809243cdc5d)   
 [MDX Scripting Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Scripting-Fundamentals--Analysis-Services-.md)