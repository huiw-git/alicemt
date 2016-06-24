---
title: Add Reference Dialog Box
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7bdd2eee-195a-4a2f-a0aa-56f7e90c1fb4
---
# Add Reference Dialog Box
  Use the **Add Reference** dialog box to add references to a custom assembly or [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/includes/dnprdnshort_md.md)] component to your report. After you add an assembly reference, you can write expressions or embedded custom code that includes fully qualified references to classes or methods in the assembly or component. For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Custom-Code-and-Assembly-References-in-Expressions-in-Report-Designer--SSRS-.md) or [Add an Assembly Reference to a Report &#40;SSRS&#41;](../../Topics/TopicNameContainA/Add-an-Assembly-Reference-to-a-Report--SSRS-.md).  
  
1. To open the **Add Reference** dialog:
2. In the **Report** menu, click **Report Properties**
3. Click the **References** tab. 
  
## Options
After you click the **Add**:
 
 **.NET**  
 Use to select a [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/includes/dnprdnshort_md.md)] component or an assembly installed in the global assembly cache (GAC).  
  
 **Browse**  
 Use to browse to an external assembly on your file system.  
  
> [!NOTE]  
>  When you publish a report that includes a reference to an external assembly, the assembly must be installed on the report server before the report can be processed successfully.  
  
 **Recent**  
 Use to select the name of a recently used assembly.  
  
## See Also  
 [Add Code to a Report](../../Topics/TopicNameContainA/Add-Code-to-a-Report--SSRS-.md)  
[Add an Assembly reference to a report](../../Topics/TopicNameContainA/Add-an-Assembly-Reference-to-a-Report--SSRS-.md)  
  