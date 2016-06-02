---
title: Create a New Relational Mining Structure
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
---
# Create a New Relational Mining Structure
  Use the Data Mining Wizard to create a new mining structure, using data from a relational database or other source, and then save the structure and any related models to a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database.  
  
## To create a relational mining structure  
  
1.  In Solution Explorer, right\-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, and then click **New Mining Structure**.  
  
     The Data Mining Wizard opens.  
  
2.  On the **Welcome to the Data Mining Wizard** page, click **Next**.  
  
3.  On the **Select the Definition Method** page, select **From existing relational database or data warehouse**, and then click **Next**.  
  
4.  On the **Select the Data Mining Technique** page, select the data mining algorithm that you want to use, and then click **Next**.  
  
     For more information about data mining algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
5.  On the **Select Data Source View** page, under **Available data source views**, click the data source view that you want to use, and then click **Next**.  
  
     For more information about creating a data source view, see [Data Source Views in Multidimensional Models](../../Topics\TopicNameNotContainA/Data-Source-Views-in-Multidimensional-Models.md).  
  
6.  On the **Specify Table Types** page, under **Input tables**, select a case table and a nested table.  
  
7.  On the **Specify the Training Data** page, under **Mining model structure**, select the key, input, and predictable columns.  
  
     After you select the predictable column, you can click the **Suggest** button to open the **Suggest Related Columns** dialog box. You can accept the suggested columns by clicking **OK** in this dialog box to include the selected columns in the mining structure, or you can change the selections in the **Input** column first, and then click **OK**. To ignore the suggestions, click **Cancel**.  
  
8.  Click **Next**.  
  
9. On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, you can adjust the content type and data type for each column.  
  
    > [!NOTE]  
    >  You can click **Detect** to automatically detect whether a column contains continuous or discrete data. After you click this button, the column content and data types will be updated in the **Content Type** and **Data Type** columns. For more information about content types and data types, see [Content Types &#40;Data Mining&#41;](../Topic/Content%20Types%20\(Data%20Mining\).md) and [Data Types &#40;Data Mining&#41;](../Topic/Data%20Types%20\(Data%20Mining\).md).  
  
10. Click **Next**.  
  
11. On the **Completing the Wizard** page, provide a name for the mining structure and the related initial mining model that will be created, and then click **Finish**.  
  
## See Also  
 [Mining Structure Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Structure-Tasks-and-How-tos.md)  
  
  