---
title: Display an Actual Execution Plan
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
---
# Display an Actual Execution Plan
  This topic describes how to generate actual graphical execution plans by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. When actual execution plans are generated, the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries or batches execute. The execution plan that is generated displays the actual query execution plan that the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] uses to execute the queries.  
  
 To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.  
  
### To include an execution plan for a query during execution  
  
1.  On the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] toolbar, click **Database Engine Query**. You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.  
  
2.  Enter the query for which you would like to display the actual execution plan.  
  
3.  On the **Query** menu, click **Include Actual Execution Plan** or click the **Include Actual Execution Plan** toolbar button  
  
4.  Execute the query by clicking the **Execute** toolbar button. The plan used by the query optimizer is displayed on the **Execution Plan** tab in the results pane. Pause the mouse over the logical and physical operators to view the description and properties of the operators in the displayed ToolTip.  
  
     Alternatively, you can view operator properties in the Properties window. If Properties is not visible, right\-click an operator and select **Properties**. Select an operator to view its properties.  
  
5.  You can alter the display of the execution plan by right\-clicking the execution plan and selecting **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**. **Zoom In** and **Zoom Out** allow you to zoom in or out on the execution plan, while **Custom Zoom** allows you to define your own zoom, such as zooming at 80 percent. **Zoom to Fit** magnifies the execution plan to fit the result pane.  
  
  