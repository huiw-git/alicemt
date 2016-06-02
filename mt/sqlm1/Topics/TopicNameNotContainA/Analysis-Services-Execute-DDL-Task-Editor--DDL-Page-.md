---
title: Analysis Services Execute DDL Task Editor (DDL Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
---
# Analysis Services Execute DDL Task Editor (DDL Page)
  Use the **DDL** page of the **Analysis Services Execute DDL Task Editor** dialog box to specify a connection to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project or an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database and to provide information about the source of data definition language \(DDL\) statements.  
  
 To learn about this task, see [Analysis Services Execute DDL Task](../../Topics\TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md).  
  
## Static Options  
 **Connection**  
 Select an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project or an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager in the list, or click \<**New connection...**\> and use the **Add Analysis Services Connection Manager** dialog box to create a new connection.  
  
 **Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Add-Analysis-Services-Connection-Manager-Dialog-Box-UI-Reference.md), [Analysis Services Connection Manager](../../Topics\TopicNameNotContainA/Analysis-Services-Connection-Manager.md)  
  
 **SourceType**  
 Specify the source type of the DDL statements. This property has the options listed in the following table:  
  
|Value|Description|  
|-----------|-----------------|  
|**Direct Input**|Set the source to the DDL statement stored in the **SourceDirect** text box. Selecting this value displays the dynamic options in the following section.|  
|**File Connection**|Set the source to a file that contains the DDL statement. Selecting this value displays the dynamic options in the following section.|  
|**Variable**|Set the source to a variable. Selecting this value displays the dynamic options in the following section.|  
  
## Dynamic Options  
  
### SourceType \= Direct Input  
 **Source**  
 Type the DDL statements or click the ellipsis **\(…\)** and then type the statements in the **DDL Statements** dialog box.  
  
### SourceType \= File Connection  
 **Source**  
 Select a File connection in the list, or click \<**New connection...**\> and use the **File Connection Manager** dialog box to create a new connection.  
  
 **Related Topics:** [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md)  
  
### SourceType \= Variable  
 **Source**  
 Select a variable in the list, or click \<**New variable...**\> and use the **Add Variable** dialog box to create a new variable.  
  
 **Related Topics:** [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md)  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Analysis Services Execute DDL Task Editor &#40;General Page&#41;](../Topic/Analysis%20Services%20Execute%20DDL%20Task%20Editor%20\(General%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)   
 [Analysis Services Scripting Language &#40;ASSL for XMLA&#41;](../Topic/Analysis%20Services%20Scripting%20Language%20\(ASSL%20for%20XMLA\).md)   
 [XML for Analysis  &#40;XMLA&#41; Reference](../Topic/XML%20for%20Analysis%20%20\(XMLA\)%20Reference.md)  
  
  