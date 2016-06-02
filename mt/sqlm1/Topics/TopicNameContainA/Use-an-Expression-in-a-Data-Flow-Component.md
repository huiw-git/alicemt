---
title: Use an Expression in a Data Flow Component
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
---
# Use an Expression in a Data Flow Component
  This procedure describes how to add an expression to the Conditional Split transformation or to the Derived Column transformation. The Conditional Split transformation uses expressions to define the conditions that direct data rows to a transformation output, and the Derived Column transformation uses expressions to define values assigned to columns.  
  
 To implement an expression in a transformation, the package must already include at least one Data Flow task and a source. For information about adding items to packages, see the following topics:  
  
-   [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md)  
  
-   [Add or Delete a Component in a Data Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Component-in-a-Data-Flow.md)  
  
-   [Connect Components in a Data Flow](../../Topics\TopicNameContainA/Connect-Components-in-a-Data-Flow.md)  
  
### To create an expression  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it.  
  
3.  In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the **Control Flow** tab, and then click the Data Flow task that contains the data flow in which you want to implement an expression.  
  
4.  Click the **Data Flow** tab, and drag either a Conditional Split or Derived Column transformation from the **Toolbox** to the design surface.  
  
5.  Drag the green connector from the source or a transformation to the Conditional Split or Derived Column transformation.  
  
6.  Double\-click the transformation to open its dialog box.  
  
7.  In the left pane, expand **Variables** to display system and user\-defined variables, and expand **Columns** to display the transformation input columns.  
  
8.  In the right pane, expand **Mathematical Functions**, **String Functions**, **Date\/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators** to access the functions, the casts, and the operators that the expression grammar provides.  
  
9. Depending on the transformation, do one of the following to build an expression:  
  
    -   In the **Conditional Split Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Condition** column. Alternatively, you can type an expression directly in the **Condition** column.  
  
    -   In the **Derived Column Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Expression** column. Alternatively, you can type an expression directly in the **Expression** column.  
  
        > [!NOTE]  
        >  When you remove the focus from the **Condition** column or the **Expression** column, the expression text might be highlighted to indicate that the expression syntax is incorrect.  
  
10. Click **OK** to exit the dialog box.  
  
    > [!NOTE]  
    >  If the expression is not valid, an alert appears describing the syntax errors in the expression.  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md)   
 [Conditional Split Transformation](../../Topics\TopicNameNotContainA/Conditional-Split-Transformation.md)   
 [Derived Column Transformation](../../Topics\TopicNameNotContainA/Derived-Column-Transformation.md)   
 [Data Flow Task](../../Topics\TopicNameNotContainA/Data-Flow-Task.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  