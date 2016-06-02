---
title: Foreach Loop Editor (Variable Mappings Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
---
# Foreach Loop Editor (Variable Mappings Page)
  Use the **Variables Mappings** page of the **Foreach Loop Editor** dialog box to map variables to the collection value. The value of the variable is updated with the collection values on each iteration of the loop.  
  
 To learn about how to use the Foreach Loop container in an Integration Services package,  see [Foreach Loop Container](../../Topics\TopicNameNotContainA/Foreach-Loop-Container.md) . To learn about how to configure it, see [Configure a Foreach Loop Container](../../Topics\TopicNameContainA/Configure-a-Foreach-Loop-Container.md).  
  
 The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] tutorial, Creating a Simple ETL Package Tutorial, includes a lesson that teaches you to add and configure a Foreach Loop.  
  
## Options  
 **Variable**  
 Select an existing variable, or click \<**New variable...**\> to create a new variable.  
  
> [!NOTE]  
>  After you map a variable, a new row is automatically added to the **Variable** list.  
  
 **Related Topics**: [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md), [Add Variable](../../Topics\TopicNameNotContainA/Add-Variable.md)  
  
 **Index**  
 If using the Foreach Item enumerator, specify the index of the column in the collection value to map to the variable. For other enumerator types, the index is read\-only.  
  
> [!NOTE]  
>  The index is 0\-based.  
  
 **Related Topics**: [Loop through Excel Files and Tables by Using a Foreach Loop Container](../../Topics\TopicNameContainA/Loop-through-Excel-Files-and-Tables-by-Using-a-Foreach-Loop-Container.md)  
  
 **Delete**  
 Select a variable, and then click **Delete**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Foreach Loop Editor &#40;General Page&#41;](../Topic/Foreach%20Loop%20Editor%20\(General%20Page\).md)   
 [Foreach Loop Editor &#40;Collection Page&#41;](../Topic/Foreach%20Loop%20Editor%20\(Collection%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)   
 [For Loop Container](../../Topics\TopicNameNotContainA/For-Loop-Container.md)  
  
  