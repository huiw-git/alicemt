---
title: Specify Table Types (Data Mining Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
---
# Specify Table Types (Data Mining Wizard)
  Use the **Specify Table Types** page to identify the tables to use to define the mining structure. If a table is not selected, it will not be used to define the mining structure.  
  
> [!NOTE]  
>  You can add tables later from the **Mining Structure** tab in **Data Mining Designer**.  
  
 **For More Information:** [Nested Tables &#40;Analysis Services - Data Mining&#41;](../Topic/Nested%20Tables%20\(Analysis%20Services%20-%20Data%20Mining\).md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20\(Analysis%20Services%20-%20Data%20Mining\).md), [Create a Relational Mining Structure](../../Topics\TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Tables**  
 Displays the tables in the data source view that you selected on the **Select Data Source View** page of the wizard.  
  
 **Case**  
 Select one table to use as the case table.  
  
 **Nested**  
 Select the tables to use as nested tables.  
  
> [!NOTE]  
>  These tables must have a many\-to\-one relationship with the case table, not a one\-to\-many relationship. You must specify this relationship in the data source view before you can select the table as nested.  
  
## See Also  
 [Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Select Data Source View &#40;Data Mining Wizard&#41;](../Topic/Select%20Data%20Source%20View%20\(Data%20Mining%20Wizard\).md)   
 [Specify the Training Data &#40;Data Mining Wizard&#41;](../Topic/Specify%20the%20Training%20Data%20\(Data%20Mining%20Wizard\).md)  
  
  