---
title: Completing the Wizard (Data Mining Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6aef1548-35eb-42fd-ae87-63650a79eda1
---
# Completing the Wizard (Data Mining Wizard)
  Use the **Completing the Wizard** page to review the mining structure that will be created when you finish the wizard. You can also set the name of the mining structure.  
  
 If you opted to create an associated mining model, you can also set the name of the associated mining model, and enable drillthrough on the mining model.  
  
> [!NOTE]  
>  This page changes depending on whether you selected **From existing relational database or data warehouse** or **From existing cube** on the **Select the Definition Method** page of the wizard.  
  
 **For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20\(Analysis%20Services%20-%20Data%20Mining\).md), [Data Mining Designer](../../Topics\TopicNameNotContainA/Data-Mining-Designer.md), [Create a Relational Mining Structure](../../Topics\TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Mining structure name**  
 Type the name of the mining structure defined by the **Data Mining Wizard**.  
  
 **Mining model name**  
 Type the name of the mining model defined by the **Data Mining Wizard**.  
  
 **Allow Drill Through**  
 Select to support drillthrough capabilities in the new mining model, if you created one.  
  
> [!NOTE]  
>  Drillthrough on the mining structure is enabled by default.  
  
 For more information about drillthrough options, see [Drillthrough Queries &#40;Data Mining&#41;](../Topic/Drillthrough%20Queries%20\(Data%20Mining\).md).  
  
 **Preview**  
 Displays the mining structure to be created.  
  
 **Create Mining Model Dimension**  
 Select to create a dimension based on the mining model to be created. After you select this option, enter the name of the dimension to be created. Selecting this option will enable **Create cube using mining model dimension**.  
  
> [!NOTE]  
>  This option is available if you selected **From existing cube** on the **Select the Definition Method** page of the wizard.  
  
 **Create cube using mining model dimension**  
 Select to create a cube based on the mining model to be created. After you select this option, enter the name of the cube to be created.  
  
> [!NOTE]  
>  This option is available if you selected **From existing cube** on the **Select the Definition Method** page and if you have selected **Create Mining Model Dimension** on the current page of the wizard.  
  
## See Also  
 [Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Select Data Source View &#40;Data Mining Wizard&#41;](../Topic/Select%20Data%20Source%20View%20\(Data%20Mining%20Wizard\).md)   
 [Specify the Training Data &#40;Data Mining Wizard&#41;](../Topic/Specify%20the%20Training%20Data%20\(Data%20Mining%20Wizard\).md)  
  
  