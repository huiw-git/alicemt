---
title: "Foreach Loop Editor (Variable Mappings Page)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
caps.latest.revision: 38
caps.handback.revision: 0
manager: jhubbard
---
# Foreach Loop Editor (Variable Mappings Page)
Use the **Variables Mappings** page of the **Foreach Loop Editor** dialog box to map variables to the collection value. The value of the variable is updated with the collection values on each iteration of the loop.  
  
 To learn about how to use the Foreach Loop container in an Integration Services package,  see [Foreach Loop Container](../../Topics/TopicNameNotContainA/Foreach-Loop-Container.md) . To learn about how to configure it, see [Configure a Foreach Loop Container](../../Topics/TopicNameContainA/Configure-a-Foreach-Loop-Container.md).  
  
 The [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] tutorial, Creating a Simple ETL Package Tutorial, includes a lesson that teaches you to add and configure a Foreach Loop.  
  
## Options  
 **Variable**  
 Select an existing variable, or click <**New variable...**> to create a new variable.  
  
> [!NOTE]  
>  After you map a variable, a new row is automatically added to the **Variable** list.  
  
 **Related Topics**: [Integration Services (SSIS) Variables](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Variables.md), [Add Variable](../../Topics/TopicNameNotContainA/Add-Variable.md)  
  
 **Index**  
 If using the Foreach Item enumerator, specify the index of the column in the collection value to map to the variable. For other enumerator types, the index is read-only.  
  
> [!NOTE]  
>  The index is 0-based.  
  
 **Related Topics**: [Loop through Excel Files and Tables by Using a Foreach Loop Container](../../Topics/TopicNameContainA/Loop-through-Excel-Files-and-Tables-by-Using-a-Foreach-Loop-Container.md)  
  
 **Delete**  
 Select a variable, and then click **Delete**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Foreach Loop Editor (General Page)](../../Topics/TopicNameNotContainA/Foreach-Loop-Editor--General-Page-.md)   
 [Foreach Loop Editor (Collection Page)](../../Topics/TopicNameNotContainA/Foreach-Loop-Editor--Collection-Page-.md)   
 [Expressions Page](../../Topics/TopicNameNotContainA/Expressions-Page.md)   
 [For Loop Container](../../Topics/TopicNameNotContainA/For-Loop-Container.md)