---
title: "Analysis Services Execute DDL Task Editor (DDL Page)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# Analysis Services Execute DDL Task Editor (DDL Page)
Use the **DDL** page of the **Analysis Services Execute DDL Task Editor** dialog box to specify a connection to an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project or an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database and to provide information about the source of data definition language (DDL) statements.  
  
 To learn about this task, see [Analysis Services Execute DDL Task](../../Topics/TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md).  
  
## Static Options  
 **Connection**  
 Select an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project or an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] connection manager in the list, or click <**New connection...**> and use the **Add Analysis Services Connection Manager** dialog box to create a new connection.  
  
 **Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](../../Topics/TopicNameNotContainA/Add-Analysis-Services-Connection-Manager-Dialog-Box-UI-Reference.md), [Analysis Services Connection Manager](../../Topics/TopicNameNotContainA/Analysis-Services-Connection-Manager.md)  
  
 **SourceType**  
 Specify the source type of the DDL statements. This property has the options listed in the following table:  
  
|Value|Description|  
|-----------|-----------------|  
|**Direct Input**|Set the source to the DDL statement stored in the **SourceDirect** text box. Selecting this value displays the dynamic options in the following section.|  
|**File Connection**|Set the source to a file that contains the DDL statement. Selecting this value displays the dynamic options in the following section.|  
|**Variable**|Set the source to a variable. Selecting this value displays the dynamic options in the following section.|  
  
## Dynamic Options  
  
### SourceType = Direct Input  
 **Source**  
 Type the DDL statements or click the ellipsis **(…)** and then type the statements in the **DDL Statements** dialog box.  
  
### SourceType = File Connection  
 **Source**  
 Select a File connection in the list, or click <**New connection...**> and use the **File Connection Manager** dialog box to create a new connection.  
  
 **Related Topics:** [File Connection Manager](../../Topics/TopicNameNotContainA/File-Connection-Manager.md)  
  
### SourceType = Variable  
 **Source**  
 Select a variable in the list, or click <**New variable...**> and use the **Add Variable** dialog box to create a new variable.  
  
 **Related Topics:** [Integration Services (SSIS) Variables](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Variables.md)  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Analysis Services Execute DDL Task Editor (General Page)](../../Topics/TopicNameNotContainA/Analysis-Services-Execute-DDL-Task-Editor--General-Page-.md)   
 [Expressions Page](../../Topics/TopicNameNotContainA/Expressions-Page.md)   
 [Control Flow](../../Topics/TopicNameNotContainA/Control-Flow.md)   
 [Analysis Services Scripting Language Reference](assetId:///ca0e852e-9002-4224-a0f0-bd96f2fc5c65)   
 [XML for Analysis Reference (XMLA)](assetId:///88045e05-ce47-4e28-999b-7f9c74af9faf)