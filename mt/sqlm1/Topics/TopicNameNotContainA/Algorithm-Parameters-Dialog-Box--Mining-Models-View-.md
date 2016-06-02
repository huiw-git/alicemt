---
title: Algorithm Parameters Dialog Box (Mining Models View)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
---
# Algorithm Parameters Dialog Box (Mining Models View)
  Use the **Algorithm Parameters** dialog box to adjust algorithm parameters that are specific to the selected model. When you change an algorithm parameter, you will usually change the results of the mining model. The way that each parameter affects the results depends on the algorithm you are using, and on your data. For more information, see [Customize Mining Models and Structure](../../Topics\TopicNameNotContainA/Customize-Mining-Models-and-Structure.md).  
  
## Options  
 **Parameters**  
 Lists the parameters that are available for the selected mining model.  
  
 The following list describes the available columns.  
  
|Column|Description|  
|------------|-----------------|  
|**Parameter**|List the name of the parameter.|  
|**Value**|Enter a value only if you want to change the default value of the parameter.|  
|**Default**|List the default value of the parameter that the algorithm will use if you do not supply a value in the **Value** column.|  
|**Range**|List the range of possible values that you can enter into the **Value** column. The ranges can be one of the following forms:<br /><br /> a discrete list, such as 1, 2, 3<br /><br /> an inclusive range, such as \[0, 100\]<br /><br /> an exclusive range, such as \(0,...\)<br /><br /> a combination, such as \[0,...\)|  
  
 **Description**  
 Describes the selected parameter in the **Parameters** list.  
  
 **Add**  
 Click to add additional, algorithm specific\-parameters to the list. After adding the parameter, you can enter the correct name in the **Parameter** column and provide a value in the **Value** column.  
  
 **Remove**  
 Click to delete a custom parameter from the list.  
  
 If you delete one of the standard Analysis Services algorithm parameters from the list, the parameter will still be used in the model, but with the default values for that parameter. The parameter is not permanently deleted and will appear the next time that you open the dialog box.  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Models View &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Models%20View%20\(Data%20Mining%20Model%20Designer\).md)   
 [Moving Data Mining Objects](../../Topics\TopicNameNotContainA/Moving-Data-Mining-Objects.md)  
  
  