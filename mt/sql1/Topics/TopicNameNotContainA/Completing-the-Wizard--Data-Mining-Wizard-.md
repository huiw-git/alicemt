---
title: "Completing the Wizard (Data Mining Wizard)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6aef1548-35eb-42fd-ae87-63650a79eda1
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# Completing the Wizard (Data Mining Wizard)
Use the **Completing the Wizard** page to review the mining structure that will be created when you finish the wizard. You can also set the name of the mining structure.  
  
 If you opted to create an associated mining model, you can also set the name of the associated mining model, and enable drillthrough on the mining model.  
  
> [!NOTE]  
>  This page changes depending on whether you selected **From existing relational database or data warehouse** or **From existing cube** on the **Select the Definition Method** page of the wizard.  
  
 **For More Information:** [Data Mining Wizard (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard--Analysis-Services---Data-Mining-.md), [Data Mining Designer](../../Topics/TopicNameNotContainA/Data-Mining-Designer.md), [Create a Relational Mining Structure](../../Topics/TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Mining structure name**  
 Type the name of the mining structure defined by the **Data Mining Wizard**.  
  
 **Mining model name**  
 Type the name of the mining model defined by the **Data Mining Wizard**.  
  
 **Allow Drill Through**  
 Select to support drillthrough capabilities in the new mining model, if you created one.  
  
> [!NOTE]  
>  Drillthrough on the mining structure is enabled by default.  
  
 For more information about drillthrough options, see [Drillthrough Queries (Data Mining)](../../Topics/TopicNameNotContainA/Drillthrough-Queries--Data-Mining-.md).  
  
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
 [Data Mining Wizard F1 Help (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard-F1-Help--Analysis-Services---Data-Mining-.md)   
 [Select Data Source View (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Select-Data-Source-View--Data-Mining-Wizard-.md)   
 [Specify the Training Data (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Specify-the-Training-Data--Data-Mining-Wizard-.md)