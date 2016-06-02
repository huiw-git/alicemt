---
title: Expressions Page
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
---
# Expressions Page
  Use the **Expressions** page to edit property expressions and to access the **Property Expressions Editor** and **Property Expression Builder** dialog boxes.  
  
 Property expressions update the values of properties when the package is run. Property expressions can be used with the properties of packages, tasks, containers, connection managers, as well as some data flow components. The expressions are evaluated and their results are used instead of the values to which you set the properties when you configured the package and package objects. The expressions can include variables and the functions and operators that the expression language provides. For example, you can generate the subject line for the Send Mail task by concatenating the value of a variable that contains the string "Weather forecast for " and the return results of the GETDATE\(\) function to make the string "Weather forecast for 4\/5\/2006".  
  
 To learn more about writing expressions and using property expressions, see [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md) and [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md).  
  
## Options  
 **Expressions \(…\)**  
 Click the ellipsis to open the **Property Expressions Editor** dialog box. For more information, see [Property Expressions Editor](../../Topics\TopicNameNotContainA/Property-Expressions-Editor.md).  
  
 **\<property name\>**  
 Click the ellipsis to open the **Expression Builder** dialog box. For more information, see [Expression Builder](../../Topics\TopicNameNotContainA/Expression-Builder.md).  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md)   
 [System Variables](../../Topics\TopicNameNotContainA/System-Variables.md)   
 [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md)  
  
  