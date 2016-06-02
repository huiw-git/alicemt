---
title: Connect Tasks and Containers by Using a Default Precedence Constraint
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
---
# Connect Tasks and Containers by Using a Default Precedence Constraint
  Precedence constraints connect two executables. An executable can be any task or a For Loop, Foreach Loop, or Sequence container. This procedure describes how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints.  
  
## Creating Default Precedence Constraints  
 When you first use [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, the default value of a precedence constraint is **Success**. Follow these steps to configure [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer to use a different default value for precedence constraints.  
  
#### To set the default value for precedence constraints  
  
1.  Open [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
2.  On the **Tools** menu, click **Options**.  
  
3.  In the **Options** dialog box, expand **Business Intelligence Designers,** and then expand **Integration Services Designers**.  
  
4.  Click **Control Flow Auto Connect** and select **Connect a new shape to the selected shape by default**.  
  
5.  In the drop\-down list, choose either **Use a Failure constraint for the new shape** or **Use a Completion constraint for the new shape**.  
  
6.  Click **OK**.  
  
#### To create a default precedence constraint  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it.  
  
3.  Click the **Control Flow** tab.  
  
4.  On the design surface of the **Control Flow** tab, click the task or container and drag its connector to the executable to which you want the precedence constraint to apply.  
  
5.  To save the updated package, click **Save Selected Items** on the **File** menu.  
  
## See Also  
 [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md)   
 [Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../Topics\TopicNameContainA/Set-the-Value-of-a-Precedence-Constraint-by-Using-the-Shortcut-Menu.md)   
 [Set the Properties of a Precedence Constraint](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Precedence-Constraint.md)   
 [Use an Expression in a Precedence Constraint](../../Topics\TopicNameContainA/Use-an-Expression-in-a-Precedence-Constraint.md)  
  
  