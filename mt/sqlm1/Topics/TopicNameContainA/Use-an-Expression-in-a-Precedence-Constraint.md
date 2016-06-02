---
title: Use an Expression in a Precedence Constraint
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
---
# Use an Expression in a Precedence Constraint
  This procedure describes how to add an expression to a precedence constraint by using the **Precedence Constraint Editor** dialog box. Before you can add an expression to a precedence constraint, the package must include at least two executables, either tasks or containers, and they must be connected by a precedence constraint.  
  
### To add an expression to a precedence constraint  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it.  
  
3.  Click the **Control Flow** tab.  
  
4.  On the design surface of the **Control Flow** tab, double\-click the precedence constraint. The **Precedence Constraint Editor** opens.  
  
5.  Select **Expression**, **Expression and Constraint**, or **Expression or Constraint** in the **Evaluation operation** list.  
  
6.  Type an expression in the **Expression** text box or launch the Expression Builder to create an expression.  
  
7.  To validate the expression syntax, click **Test**.  
  
8.  To save the updated package, click **Save Selected Items** on the **File** menu.  
  
## See Also  
 [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md)   
 [Connect Tasks and Containers by Using a Default Precedence Constraint](../../Topics\TopicNameContainA/Connect-Tasks-and-Containers-by-Using-a-Default-Precedence-Constraint.md)   
 [Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../Topics\TopicNameContainA/Set-the-Value-of-a-Precedence-Constraint-by-Using-the-Shortcut-Menu.md)   
 [Set the Properties of a Precedence Constraint](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Precedence-Constraint.md)   
 [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md)  
  
  