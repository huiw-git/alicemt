---
title: Configure a For Loop Container
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
---
# Configure a For Loop Container
  This procedure describes how to configure a For Loop container by using the **For Loop Editor** dialog box.  
  
 For an example of the For Loop container, see [SSIS Loops that do not fail](http://go.microsoft.com/fwlink/?LinkId=240295) on bimonkey.com.  
  
### To configure the For Loop container  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], double\-click the For Loop container to open the **For Loop Editor**.  
  
2.  Optionally, modify the name and description of the For Loop container.  
  
3.  Optionally, type an initialization expression in the **InitExpression** text box.  
  
4.  Type an evaluation expression in the **EvalExpression** text box.  
  
    > [!NOTE]  
    >  The expression must evaluate to a Boolean. When the expression evaluates to **false**, the loop stops running.  
  
5.  Optionally, type an assignment expression in the **AssignExpression** text box.  
  
6.  Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the For Loop container. For more information, see [Add or Change a Property Expression](../../Topics\TopicNameContainA/Add-or-Change-a-Property-Expression.md).  
  
7.  Click **OK** to close the **For Loop Editor**.  
  
## See Also  
 [For Loop Container](../../Topics\TopicNameNotContainA/For-Loop-Container.md)   
 [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md)   
 [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md)  
  
  