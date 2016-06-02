---
title: Add or Change a Property Expression
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb5da499-065f-4fa6-9f6d-5bc5f385241e
---
# Add or Change a Property Expression
  You can create property expressions for packages, tasks, Foreach Loop containers, For Loop containers, Sequence containers, event handlers, package and project level connection managers, and log providers.  
  
 To create or change property expressions, you can use either the **Property Expressions Editor** or **Expression Builder**. The **Property Expressions Editor** can be accessed from either the custom editors that are available for tasks and containers, or from the **Properties** window. **Expression Builder** can be accessed from inside the **Property Expressions Editor**. While you can write expressions in either the **Property Expressions Editor** or **Expression Builder**, **Expression Builder** provides a graphical set of tools that makes it simple to build complex expressions.  
  
 To learn more about the syntax, operators, and functions that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides, see [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md) and [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md). The topic for each operator or function includes examples of using that operator or function in an expression. For examples of more complex expressions, see [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md).  
  
### To create or change a property expression  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the project that contains the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package you want.  
  
2.  In Solution Explorer, double\-click the package to open it, and then do one of the following:  
  
    -   If the item is a task or a container, double\-click the item, and then click **Expressions** in the editor.  
  
    -   Right\-click the item and then click **Properties**.  
  
3.  Click in the **Expressions** box and then click the ellipsis \(…\).  
  
4.  In the **Property Expressions Editor**, select a property in the **Property** list, and then do one of the following:  
  
    -   Type or change the property expression directly in the **Expression** column, and then click **OK**.  
  
         —or—  
  
    -   Click the ellipsis \(…\) in the expression row of the property to open the **Expression Builder**.  
  
5.  \(Optional\) In the **Expression Builder**, do any of the following tasks:  
  
    -   To access system and user\-defined variables, expand **Variables**.  
  
    -   To access the functions, the casts, and the operators that the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] expression language provides, expand **Mathematical Functions**, **String Functions**, **Date\/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators**.  
  
    -   To build or change an expression in the **Expression Builder**, drag variables, columns, functions, operators, and casts to the **Expression** box, or type the expression in the box.  
  
    -   To view the evaluation result of the expression, click **Evaluate Expression** in the **Expression Builder**.  
  
         If the expression is not valid, an alert appears that describes the syntax errors in the expression.  
  
        > [!NOTE]  
        >  Evaluating an expression does not assign the evaluation result to the property.  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md)   
 [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md)   
 [Integration Services &#40;SSIS&#41; Packages](../Topic/Integration%20Services%20\(SSIS\)%20Packages.md)   
 [Integration Services Containers](../../Topics\TopicNameNotContainA/Integration-Services-Containers.md)   
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Integration Services &#40;SSIS&#41; Event Handlers](../Topic/Integration%20Services%20\(SSIS\)%20Event%20Handlers.md)   
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)   
 [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md)  
  
  