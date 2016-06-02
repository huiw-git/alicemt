---
title: Specify the Training Data (Data Mining Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
---
# Specify the Training Data (Data Mining Wizard)
  Use the **Specify the Training Data** page to identify which columns to include in the mining structure. You can select columns to include in the structure even if you do not use them in all models. For example, if you want to drill through to the columns from the mining model, you can include them in the structure but not in the model.  
  
 At least one key column is required for each table that is included in the structure. The column that you pick as the key depends on whether the table is a case table or a nested table. If the table is a nested table, the key is often also the predictable column, not the relational foreign key. To learn about nested keys, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../Topic/Nested%20Tables%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
> [!NOTE]  
>  Different mining algorithms use keys differently. To learn about the different kinds of keys, see [Content Types &#40;Data Mining&#41;](../Topic/Content%20Types%20\(Data%20Mining\).md).  
  
 **For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md), [Mining Model Columns](../../Topics\TopicNameNotContainA/Mining-Model-Columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20\(Analysis%20Services%20-%20Data%20Mining\).md), [Create a Relational Mining Structure](../../Topics\TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Tables\/Columns**  
 Displays the tables and columns that you selected on the previous page of the wizard.  
  
 **\<check box\>**  
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
 [Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Suggest Related Columns &#40;Data Mining Wizard&#41;](../Topic/Suggest%20Related%20Columns%20\(Data%20Mining%20Wizard\).md)   
 [Specify Table Types &#40;Data Mining Wizard&#41;](../Topic/Specify%20Table%20Types%20\(Data%20Mining%20Wizard\).md)   
 [Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;](../Topic/Specify%20the%20Column's%20Content%20and%20Data%20Type%20\(Data%20Mining%20Wizard\).md)  
  
  