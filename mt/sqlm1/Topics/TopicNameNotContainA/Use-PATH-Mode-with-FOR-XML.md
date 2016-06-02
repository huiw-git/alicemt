---
title: Use PATH Mode with FOR XML
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
---
# Use PATH Mode with FOR XML
  As described in [Constructing XML Using FOR XML](../Topic/FOR%20XML%20\(SQL%20Server\).md), the PATH mode provides a simpler way to mix elements and attributes. PATH mode is also a simpler way to introduce additional nesting for representing complex properties. You can use FOR XML EXPLICIT mode queries to construct such XML from a rowset, but the PATH mode provides a simpler alternative to the potentially cumbersome EXPLICIT mode queries. PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.  
  
 In PATH mode, column names or column aliases are treated as XPath expressions. These expressions indicate how the values are being mapped to XML. Each XPath expression is a relative XPath that provides the item type., such as the attribute, element, and scalar value, and the name and hierarchy of the node that will be generated relative to the row element.  
  
 This section describes mapping columns in a rowset under various conditions, and provides examples.  
  
## In This Section  
  
-   [Columns without a Name](../../Topics\TopicNameContainA/Columns-without-a-Name.md)  
  
-   [Columns with a Name](../../Topics\TopicNameContainA/Columns-with-a-Name.md)  
  
-   [Columns with a Name Specified as a Wildcard Character](../../Topics\TopicNameContainA/Columns-with-a-Name-Specified-as-a-Wildcard-Character.md)  
  
-   [Columns with the Name of an XPath Node Test](../../Topics\TopicNameNotContainA/Columns-with-the-Name-of-an-XPath-Node-Test.md)  
  
-   [Column Names with the Path Specified as data&#40;&#41;](../Topic/Column%20Names%20with%20the%20Path%20Specified%20as%20data\(\).md)  
  
-   [Columns that Contain a Null Value By Default](../../Topics\TopicNameContainA/Columns-that-Contain-a-Null-Value-By-Default.md)  
  
-   [Namespace Support in PATH Mode](../../Topics\TopicNameNotContainA/Namespace-Support-in-PATH-Mode.md)  
  
-   [Examples: Using PATH Mode](../Topic/Examples:%20Using%20PATH%20Mode.md)  
  
## See Also  
 [Add Namespaces to Queries with WITH XMLNAMESPACES](../../Topics\TopicNameNotContainA/Add-Namespaces-to-Queries-with-WITH-XMLNAMESPACES.md)   
 [SELECT &#40;Transact-SQL&#41;](../Topic/SELECT%20\(Transact-SQL\).md)   
 [FOR XML &#40;SQL Server&#41;](../Topic/FOR%20XML%20\(SQL%20Server\).md)  
  
  