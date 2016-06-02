---
title: For Loop Container
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
---
# For Loop Container
  The For Loop container defines a repeating control flow in a package. The loop implementation is similar to the **For** looping structure in programming languages. In each repeat of the loop, the For Loop container evaluates an expression and repeats its workflow until the expression evaluates to **False**.  
  
 The For Loop container usesthe following elements to define the loop:  
  
-   An optional initialization expression that assigns values to the loop counters.  
  
-   An evaluation expression that contains the expression used to test whether the loop should stop or continue.  
  
-   An optional iteration expression that increments or decrements the loop counter.  
  
 The following diagram shows a For Loop container with a Send Mail task. If the initialization expression is `@Counter = 0`, the evaluation expression is `@Counter < 4`, and the iteration expression is `@Counter = @Counter + 1`, the loop repeats four times and sends four e\-mail messages.  
  
 ![A For Loop container repeats a task four times](../../Images\Image\ImageContaina/SSIS_ForLoop.gif "SSIS_ForLoop")  
  
 The expressions must be valid [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] expressions.  
  
 To create the initialization and assignment expressions, you can use the assignment operator \(\=\). This operator is not otherwise supported by the Integration Services expression grammar and can only be used by the initialization and assignment expression types in the For Loop container. Any expression that uses the assignment operator must have the syntax `@Var = <expression>`, where **Var** is a run\-time variable and \<expression\> is an expression that follows the rules of the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] expression syntax. The expression can include the variables, literals, and any operators and functions that the SSIS expression grammar supports. The expression must evaluate to a data type that can be cast to the data type of the variable.  
  
 A For Loop container can have only one evaluation expression. This means that the For Loop container runs all its control flow elements the same number of times. Because the For Loop container can include other For Loop containers, you can build nested loops and implement complex looping in packages.  
  
 You can set a transaction property on the For Loop container to define a transaction for a subset of the package control flow. In this way, you can manage transactions at a more granular level. For example, if a For Loop container repeats a control flow that updates data in a table multiple times, you can configure the For Loop and its control flow to use a transaction to ensure that if not all data is updated successfully, no data is updated. For more information, see [Integration Services Transactions](../../Topics\TopicNameNotContainA/Integration-Services-Transactions.md).  
  
## Configuration of the For Loop Container  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [For Loop Editor](../../Topics\TopicNameNotContainA/For-Loop-Editor.md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For more information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** class in the Developer Guide.  
  
## Related Tasks  
 For information about how to configure a For Loop Container, see the following topics.  
  
-   [Configure a For Loop Container](../../Topics\TopicNameContainA/Configure-a-For-Loop-Container.md)  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## See Also  
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)   
 [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md)  
  
  