---
title: "Querying Multidimensional Data with MDX"
ms.custom: 
  - SQL2016_New_Updated
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
ms.assetid: e0a5dd60-35a3-4a4f-b36f-52ecea814886
caps.latest.revision: 18
caps.handback.revision: 0
manager: mblythe
---
# Querying Multidimensional Data with MDX
Multidimensional Expressions (MDX) is the query language that you use to work with and retrieve multidimensional data in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]. MDX is based on the XML for Analysis (XMLA) specification, with specific extensions for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]. MDX utilizes expressions composed of identifiers, values, statements, functions, and operators that [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] can evaluate to retrieve an object (for example a set or a member), or a scalar value (for example, a string or a number).  
  
 MDX queries and expressions in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] are used to do the following:  
  
-   Return data to a client application from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] cube.  
  
-   Format query results.  
  
-   Perform cube design tasks, including the definition of calculated members, named sets, scoped assignments, and key performance indicators (KPIs).  
  
-   Perform administrative tasks, including dimension and cell security.  
  
 MDX is superficially similar in many ways to the SQL syntax that is typically used with relational databases. However, MDX is not an extension of the SQL language and is different from SQL in many ways. In order to create MDX expressions used to design or secure cubes, or to create MDX queries to return and format multidimensional data, you need to understand basic concepts in MDX and dimensional modeling, MDX syntax elements, MDX operators, MDX statements, and MDX functions.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Key Concepts in MDX (Analysis Services)](../../Topics/TopicNameNotContainA/Key-Concepts-in-MDX--Analysis-Services-.md)|You can use Multidimensional Expressions (MDX) to query multidimensional data or to create MDX expressions for use within a cube, but first you should understand [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] dimension concepts and terminology.|  
|[MDX Query Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)|Multidimensional Expressions (MDX) enables you to query multidimensional objects, such as cubes, and return multidimensional cellsets that contain the cube's data. This topic and its subtopics provide an overview of MDX queries.|  
|[MDX Scripting Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Scripting-Fundamentals--Analysis-Services-.md)|In [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], a Multidimensional Expressions (MDX) script is made up of one or more MDX expressions or statements that populate a cube with calculations.<br /><br /> An MDX script defines the calculation process for a cube. An MDX script is also considered part of the cube itself. Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.<br /><br /> To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].|  
  
## See Also  
 [MDX Syntax Elements (MDX)](assetId:///f4c16e1a-cf1a-4be0-839a-db018430ff14)   
 [MDX Language Reference (MDX)](assetId:///8ceaedd3-7679-4300-83a5-4809243cdc5d)