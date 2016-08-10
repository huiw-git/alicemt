---
title: "Analysis Services Processing Task Editor (Analysis Services Page)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Analysis Services Processing Task Editor (Analysis Services Page)
Use the **Analysis Services** page of the **Analysis Services Processing Task Editor** dialog box to specify an Analysis Services connection manager, select the analytic objects to process, and set processing and error handling options.  
  
 When processing tabular models, keep the following in mind:  
  
1.  You cannot perform impact analysis on tabular models.  
  
2.  Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc. You can perform these functions by using the Execute DDL task.  
  
3.  Some processing options provided, such as process indexes, are not appropriate for tabular models and should not be used.  
  
4.  Batch settings are ignored for tabular models.  
  
 To learn about this task, see [Analysis Services Processing Task](../../Topics/TopicNameNotContainA/Analysis-Services-Processing-Task.md).  
  
## Options  
 **Analysis Services connection manager**  
 Select an existing Analysis Services connection manager in the list or click **New** to create a new connection manager.  
  
 **New**  
 Create a new Analysis Services connection manager.  
  
 **Related Topics:** [Analysis Services Connection Manager](../../Topics/TopicNameNotContainA/Analysis-Services-Connection-Manager.md), [Add Analysis Services Connection Manager Dialog Box UI Reference](../../Topics/TopicNameNotContainA/Add-Analysis-Services-Connection-Manager-Dialog-Box-UI-Reference.md)  
  
 **Object list**  
 |Property|Description|  
|--------------|-----------------|  
|**Object Name**|Lists the specified object names.|  
|**Type**|Lists the types of the specified objects.|  
|**Process Options**|Select a processing option in the list.<br /><br /> **Related Topics**: [Processing a multidimensional model (Analysis Services)](../../Topics/TopicNameContainA/Processing-a-multidimensional-model--Analysis-Services-.md)|  
|**Settings**|Lists processing settings for the specified objects.|  
  
 **Add**  
 Add an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] object to the list.  
  
 **Remove**  
 Select an object, and then click **Delete**.  
  
 **Impact Analysis**  
 Perform impact analysis on the selected object.  
  
 **Related Topics:** [Impact Analysis Dialog Box (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Impact-Analysis-Dialog-Box--Analysis-Services---Multidimensional-Data-.md)  
  
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
  
 **Related Topics:** [Change Settings Dialog Box (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Change-Settings-Dialog-Box--Analysis-Services---Multidimensional-Data-.md)  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Analysis Services Processing Task Editor (General Page)](../../Topics/TopicNameNotContainA/Analysis-Services-Processing-Task-Editor--General-Page-.md)   
 [Analysis Services Execute DDL Task](../../Topics/TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md)