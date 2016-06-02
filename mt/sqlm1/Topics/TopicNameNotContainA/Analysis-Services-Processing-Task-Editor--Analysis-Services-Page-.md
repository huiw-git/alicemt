---
title: Analysis Services Processing Task Editor (Analysis Services Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
---
# Analysis Services Processing Task Editor (Analysis Services Page)
  Use the **Analysis Services** page of the **Analysis Services Processing Task Editor** dialog box to specify an Analysis Services connection manager, select the analytic objects to process, and set processing and error handling options.  
  
 When processing tabular models, keep the following in mind:  
  
1.  You cannot perform impact analysis on tabular models.  
  
2.  Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc. You can perform these functions by using the Execute DDL task.  
  
3.  Some processing options provided, such as process indexes, are not appropriate for tabular models and should not be used.  
  
4.  Batch settings are ignored for tabular models.  
  
 To learn about this task, see [Analysis Services Processing Task](../../Topics\TopicNameNotContainA/Analysis-Services-Processing-Task.md).  
  
## Options  
 **Analysis Services connection manager**  
 Select an existing Analysis Services connection manager in the list or click **New** to create a new connection manager.  
  
 **New**  
 Create a new Analysis Services connection manager.  
  
 **Related Topics:** [Analysis Services Connection Manager](../../Topics\TopicNameNotContainA/Analysis-Services-Connection-Manager.md), [Add Analysis Services Connection Manager Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Add-Analysis-Services-Connection-Manager-Dialog-Box-UI-Reference.md)  
  
 **Object list**  
 |Property|Description|  
|--------------|-----------------|  
|**Object Name**|Lists the specified object names.|  
|**Type**|Lists the types of the specified objects.|  
|**Process Options**|Select a processing option in the list.<br /><br /> **Related Topics**: [Processing a multidimensional model &#40;Analysis Services&#41;](../Topic/Processing%20a%20multidimensional%20model%20\(Analysis%20Services\).md)|  
|**Settings**|Lists processing settings for the specified objects.|  
  
 **Add**  
 Add an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object to the list.  
  
 **Remove**  
 Select an object, and then click **Delete**.  
  
 **Impact Analysis**  
 Perform impact analysis on the selected object.  
  
 **Related Topics:** [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Impact%20Analysis%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
 **Batch Settings Summary**  
 |Property|Description|  
|--------------|-----------------|  
|**Processing order**|Specifies whether objects are processed sequentially or in a batch; if parallel processing is used, specifies the number of objects to process concurrently.|  
|**Transaction mode**|Specifies the transaction mode for sequential processing.|  
|**Dimension errors**|Specifies the task behavior when errors occur.|  
|**Dimension key error log path**|Specifies the path of the file to which errors are logged.|  
|**Process affected objects**|Indicates whether dependent or affected objects are also processed.|  
  
 **Change Settings**  
 Change the processing options and the handling of errors in dimension keys.  
  
 **Related Topics:** [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Change%20Settings%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Analysis Services Processing Task Editor &#40;General Page&#41;](../Topic/Analysis%20Services%20Processing%20Task%20Editor%20\(General%20Page\).md)   
 [Analysis Services Execute DDL Task](../../Topics\TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md)  
  
  