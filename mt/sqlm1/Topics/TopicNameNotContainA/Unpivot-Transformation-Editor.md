---
title: Unpivot Transformation Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
---
# Unpivot Transformation Editor
  Use the **Unpivot Transformation Editor** dialog box to select the columns to pivot into rows, and to specify the data column and the new pivot value output column.  
  
> [!NOTE]  
>  This topic relies on the Unpivot scenario described in [Unpivot Transformation](../../Topics\TopicNameNotContainA/Unpivot-Transformation.md) to illustrate the use of the options.  
  
 To learn more about the Unpivot transformation, see [Unpivot Transformation](../../Topics\TopicNameNotContainA/Unpivot-Transformation.md).  
  
## Options  
 **Available Input Columns**  
 Using the check boxes, specify the columns to pivot into rows.  
  
 **Name**  
 View the name of the available input column.  
  
 **Pass Through**  
 Indicate whether to include the column in the unpivoted output.  
  
 **Input Column**  
 Select from the list of available input columns for each row. Your selections are reflected in the check box selections in the **Available Input Columns** table.  
  
 In the Unpivot scenario described in [Unpivot Transformation](../../Topics\TopicNameNotContainA/Unpivot-Transformation.md), the Input Columns are the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns.  
  
 **Destination Column**  
 Provide a name for the data column.  
  
 In the Unpivot scenario described in [Unpivot Transformation](../../Topics\TopicNameNotContainA/Unpivot-Transformation.md), the Destination Column is the quantity \(**Qty**\) column.  
  
 **Pivot Key Value**  
 Provide a name for the pivot value. The default is the name of the input column; however, you can choose any unique, descriptive name.  
  
 The value of this property can be specified by using a property expression.  
  
 In the Unpivot scenario described in [Unpivot Transformation](../../Topics\TopicNameNotContainA/Unpivot-Transformation.md), the Pivot Values will appear in the new Product column designated by the **Pivot Key Value Column Name** option, as the text values **Ham**, **Soda**, **Milk**, **Beer**, and **Chips**.  
  
 **Pivot Key Value Column Name**  
 Provide a name for the pivot value column. The default is "Pivot Key Value"; however, you can choose any unique, descriptive name.  
  
 In the Unpivot scenario described in [Unpivot Transformation](../../Topics\TopicNameNotContainA/Unpivot-Transformation.md), the Pivot Key Value Column Name is **Product** and designates the new **Product** column into which the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns are unpivoted.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Pivot Transformation](../../Topics\TopicNameNotContainA/Pivot-Transformation.md)  
  
  