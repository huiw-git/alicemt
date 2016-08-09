---
title: "Specify the Training Data (Data Mining Wizard)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Specify the Training Data (Data Mining Wizard)
Use the **Specify the Training Data** page to identify which columns to include in the mining structure. You can select columns to include in the structure even if you do not use them in all models. For example, if you want to drill through to the columns from the mining model, you can include them in the structure but not in the model.  
  
 At least one key column is required for each table that is included in the structure. The column that you pick as the key depends on whether the table is a case table or a nested table. If the table is a nested table, the key is often also the predictable column, not the relational foreign key. To learn about nested keys, see [Nested Tables (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Nested-Tables--Analysis-Services---Data-Mining-.md).  
  
> [!NOTE]  
>  Different mining algorithms use keys differently. To learn about the different kinds of keys, see [Content Types (Data Mining)](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md).  
  
 **For More Information:** [Mining Structures (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md), [Mining Model Columns](../../Topics/TopicNameNotContainA/Mining-Model-Columns.md), [Data Mining Wizard (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard--Analysis-Services---Data-Mining-.md), [Create a Relational Mining Structure](../../Topics/TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Tables/Columns**  
 Displays the tables and columns that you selected on the previous page of the wizard.  
  
 **<check box\>**  
 Select the columns to include in the mining structure.  
  
 If your data source includes nested tables or multiple views, expand the column list to view the nested tables.  
  
 **Key**  
 Select to use the column as a unique identifier for the data.  
  
 For a case table, the key is usually the unique identifier.  
  
 For nested table, the **Key** indicates the identifier of a row in the context of the associated case.  
  
 **Input**  
 Select to use the column in creating predictions.  
  
> [!NOTE]  
>  This column is only available when you are creating a mining model together with the mining structure.  
  
 **Predictable**  
 Select to enable the table or column to be predicted based on additional future input.  
  
 If you also mark a nested table as predictable, the whole nested table becomes predictable. If no columns in the nested table are marked as input or predictable, the nested table will appear in the mining structure, but will be ignored in the model.  
  
 **Note** This column is only available when you are creating a mining model together with the mining structure.  
  
 **Suggest**  
 Click to open the **Suggest Related Columns** dialog box, which performs an analysis on a sample of data to identify input columns that show the greatest relationship to the selected **Predictable** column based on entropy. This analysis also applies to nested table columns or mining structures that are based on OLAP sources.  
  
 **Note** This column only available when you are creating a mining model together with the mining structure.  
  
## See Also  
 [Data Mining Wizard F1 Help (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard-F1-Help--Analysis-Services---Data-Mining-.md)   
 [Suggest Related Columns (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Suggest-Related-Columns--Data-Mining-Wizard-.md)   
 [Specify Table Types (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Specify-Table-Types--Data-Mining-Wizard-.md)   
 [Specify the Column's Content and Data Type (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Specify-the-Column-s-Content-and-Data-Type--Data-Mining-Wizard-.md)