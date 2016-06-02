---
title: Analysis Services Processing Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5748836-b4ce-4e17-ab6b-617a336f02f4
---
# Analysis Services Processing Task
  The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Processing task processes [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects such as tabular models, cubes, dimensions, and mining models.  
  
 When processing tabular models, keep the following in mind:  
  
-   You cannot perform impact analysis on tabular models.  
  
-   Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc. You can perform these functions by using the Execute DDL task.  
  
-   The options Process Index and Process Update are not appropriate for tabular models and should not be used.  
  
-   Batch settings are ignored for tabular models.  
  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes a number of tasks that perform business intelligence operations, such as running Data Definition Language \(DDL\) statements and data mining prediction queries. For more information about related business intelligence tasks, click one of the following topics:  
  
-   [Analysis Services Execute DDL Task](../../Topics\TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md)  
  
-   [Data Mining Query Task](../../Topics\TopicNameNotContainA/Data-Mining-Query-Task.md)  
  
## Object Processing  
 Multiple objects can be processed at the same time. When processing multiple objects, you define settings that apply to the processing of all the objects in the batch.  
  
 Objects in a batch can be processed in sequence or in parallel. If the batch does not contain objects for which processing sequence is important, parallel processing can speed up processing. If objects in the batch are processed in parallel, you can configure the task to let it determine how many objects to process in parallel, or you can manually specify the number of objects to process at the same time. If objects are processed sequentially, you can set a transaction attribute on the batch either by enlisting all objects in one transaction or by using a separate transaction for each object in the batch.  
  
 When you process analytic objects, you might also want to process the objects that depend on them. The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Processing task includes an option to process any dependent objects in addition to the selected objects.  
  
 Typically, you process dimension tables before processing fact tables. You may encounter errors if you try to process fact tables before processing the dimension tables.  
  
 This task also lets you configure the handling of errors in dimension keys. For example, the task can ignore errors or stop after a specified number of errors occur. The task can use the default error configuration, or you can construct a custom error configuration. In the custom error configuration, you specify how the task handles errors and the error conditions. For example, you can specify that the task should stop running when the fourth error occurs, or specify how the task should handle **Null** key values. The custom error configuration can also include the path of an error log.  
  
> [!NOTE]  
>  The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Processing task can process only analytic objects created by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools.  
  
 This task is frequently used in combination with a Bulk Insert task that loads data into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table, or a Data Flow task that implements a data flow that loads data into a table. For example, the Data Flow task might have a data flow that extracts data from an online transactional database \(OLTP\) database and loads it into a fact table in a data warehouse, after which the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Processing task is called to process the cube built on the data warehouse.  
  
 The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Processing task uses an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager to connect to an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. For more information, see [Analysis Services Connection Manager](../../Topics\TopicNameNotContainA/Analysis-Services-Connection-Manager.md).  
  
## Error Handling  
  
## Configuration of the Analysis Services Processing Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [Analysis Services Processing Task Editor &#40;General Page&#41;](../Topic/Analysis%20Services%20Processing%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Analysis Services Processing Task Editor &#40;Analysis Services Page&#41;](../Topic/Analysis%20Services%20Processing%20Task%20Editor%20\(Analysis%20Services%20Page\).md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For more information about setting these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## Programmatic Configuration of the Analysis Services Processing Task  
 For more information about programmatically setting these properties, click one of the following topics:  
  
-   [DTSProcessingTask](assetId:///T:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.DTSProcessingTask)  
  
  