---
title: "Specify the Column&#39;s Content and Data Type (Data Mining Wizard)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7061f674-e806-46f2-8c15-e260a3c69a17
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# Specify the Column&#39;s Content and Data Type (Data Mining Wizard)
Use the **Specify the Column's Content and Data Type** page to modify the column and content types that have already been set by the wizard. The wizard uses the data types of the source columns and the capabilities of the selected algorithm to determine the default data and content types for each column.  
  
 **For More Information:** [Data Mining Wizard (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard--Analysis-Services---Data-Mining-.md), [Create a Relational Mining Structure](../../Topics/TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Columns**  
 A list of the columns that are defined in the **Specify the Training Data** page of the wizard.  
  
 **Content Type**  
 The content type that is assigned to each column. Click inside a cell to change the content type. For more information about content types, see [Content Types (Data Mining)](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md).  
  
 **Data Type**  
 The data types that are assigned to each column. Click inside a cell to change the data type. For more information about data types, see [Data Types (Data Mining)](../../Topics/TopicNameNotContainA/Data-Types--Data-Mining-.md).  
  
 **Detect**  
 Click to automatically detect the continuous and discrete content types for numeric column. This does not apply to mining structures that are based on OLAP data sources. For OLAP mining structures, the wizard automatically detects content types and chooses a type that is compatible with the selected algorithm.  
  
## See Also  
 [Completing the Wizard (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Completing-the-Wizard--Data-Mining-Wizard-.md)   
 [Data Mining Wizard F1 Help (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard-F1-Help--Analysis-Services---Data-Mining-.md)   
 [Specify the Training Data (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Specify-the-Training-Data--Data-Mining-Wizard-.md)