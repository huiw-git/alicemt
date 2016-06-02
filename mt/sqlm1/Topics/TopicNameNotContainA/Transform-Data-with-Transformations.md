---
title: Transform Data with Transformations
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
---
# Transform Data with Transformations
  [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes three types of data flow components: sources, transformations, and destinations.  
  
 The following diagram shows a simple data flow that has a source, two transformations, and a destination.  
  
 ![Data flow](../../Images\Image\ImageNotContaina/MW_DTS_08.gif "MW_DTS_08")  
  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] transformations provide the following functionality:  
  
-   Splitting, copying, and merging rowsets and performing lookup operations.  
  
-   Updating column values and creating new columns by applying transformations such as changing lowercase to uppercase.  
  
-   Performing business intelligence operations such as cleaning data, mining text, or running data mining prediction queries.  
  
-   Creating new rowsets that consist of aggregate or sorted values, sample data, or pivoted and unpivoted data.  
  
-   Performing tasks such as exporting and importing data, providing audit information, and working with slowly changing dimensions.  
  
 For more information, see [Integration Services Transformations](../../Topics\TopicNameNotContainA/Integration-Services-Transformations.md).  
  
 You can also write custom transformations. For more information, see [Developing a Custom Data Flow Component](../Topic/Developing%20a%20Custom%20Data%20Flow%20Component.md) and [Developing Specific Types of Data Flow Components](../Topic/Developing%20Specific%20Types%20of%20Data%20Flow%20Components.md).  
  
 After you add the transformation to the data flow designer, but before you configure the transformation, you connect the transformation to the data flow by connecting the output of another transformation or source in the data flow to the input of this transformation. The connector between two data flow components is called a path. For more information about connecting components and working with paths, see [Connect Components with Paths](../../Topics\TopicNameNotContainA/Connect-Components-with-Paths.md).  
  
### To add a transformation to a data flow  
  
-   [Add or Delete a Component in a Data Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Component-in-a-Data-Flow.md)  
  
### To connect a transformation to a data flow  
  
-   [Connect Components in a Data Flow](../../Topics\TopicNameContainA/Connect-Components-in-a-Data-Flow.md)  
  
### To set the properties of a transformation  
  
-   [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md)  
  
## See Also  
 [Data Flow Task](../../Topics\TopicNameNotContainA/Data-Flow-Task.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Connect Components with Paths](../../Topics\TopicNameNotContainA/Connect-Components-with-Paths.md)   
 [Error Handling in Data](../../Topics\TopicNameNotContainA/Error-Handling-in-Data.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  