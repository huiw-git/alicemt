---
title: Data Mining Query Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f489348c-2008-4f66-8c2c-c07c3029439a
---
# Data Mining Query Task
  The Data Mining Query task runs prediction queries based on data mining models built in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. The prediction query creates a prediction for new data by using mining models. For example, a prediction query can predict how many sailboats are likely to sell during the summer months or generate a list of prospective customers who are likely to buy a sailboat.  
  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides tasks that perform other business intelligence operations, such as running Data Definition Language \(DDL\) statements and processing analytic objects.  
  
 For more information about other business intelligence tasks, click one of the following topics:  
  
-   [Analysis Services Execute DDL Task](../../Topics\TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md)  
  
-   [Analysis Services Processing Task](../../Topics\TopicNameNotContainA/Analysis-Services-Processing-Task.md)  
  
## Prediction Queries  
 The query is a Data Mining Extensions \(DMX\) statement. The DMX language is an extension of the SQL language that provides support for working with mining models. For more information about how to use the DMX language, see [Data Mining Extensions &#40;DMX&#41; Reference](../Topic/Data%20Mining%20Extensions%20\(DMX\)%20Reference.md).  
  
 The task can query multiple mining models that are built on the same mining structure. A mining model is built using one of the data mining algorithms that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides. The mining structure that the Data Mining Query task references can include multiple mining models, built using different algorithms. For more information, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md) and [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
 The prediction query that the Data Mining Query task runs returns a result that is a single row or a data set. A query that returns a single row is called a singleton query: for example, the query that predicts how many sailboats will be sold during the summer months returns a number. For more information about prediction queries that return a single row, see [Data Mining Query Tools](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tools.md).  
  
 The query results are saved to tables. If a table with the name that the Data Mining Query task specifies already exists, the task can create a new table, using the same name with a number appended, or it can overwrite the table content.  
  
 If the results include nesting, the result is flattened before it is saved. Flattening a result changes a nested result set to a table. For example, flattening a nested result with a **Customer** column and a nested **Product** column adds rows to the **Customer** column to make a table that includes product data for each customer. For example, a customer with three different products becomes a table with three rows, repeating the customer in each row and including a different product in each row. If the FLATTENED keyword is omitted, the table contains only the **Customer** column and only one row per customer. For more information, see [SELECT &#40;DMX&#41;](../Topic/SELECT%20\(DMX\).md).  
  
## Configuration of the Data Mining Query Task  
 The Data Mining Query task requires two connections. The first connection is an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager that connects either to an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] or to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project that contains the mining structure and the mining model. The second connection is an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database that contains the table to which the task writes. For more information, see [Analysis Services Connection Manager](../../Topics\TopicNameNotContainA/Analysis-Services-Connection-Manager.md) and [OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md).  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../Topic/Data%20Mining%20Query%20Task%20Editor%20\(Mining%20Model%20Tab\).md)  
  
-   [Data Mining Query Task Editor &#40;Query Tab&#41;](../Topic/Data%20Mining%20Query%20Task%20Editor%20\(Query%20Tab\).md)  
  
-   [Data Mining Query Task Editor &#40;Output Tab&#41;](../Topic/Data%20Mining%20Query%20Task%20Editor%20\(Output%20Tab\).md)  
  
> [!NOTE]  
>  The Data Mining Query Editor has no Expressions page. Instead, use the **Properties** window to access the tools for creating and managing property expressions for properties of the Data Mining Query task.  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## Programmatic Configuration of Data Mining Query Task  
 For more information about programmatically setting these properties, click one of the following topics:  
  
-   [DMQueryTask](assetId:///T:Microsoft.SqlServer.Dts.Tasks.DMQueryTask.DMQueryTask)  
  
  