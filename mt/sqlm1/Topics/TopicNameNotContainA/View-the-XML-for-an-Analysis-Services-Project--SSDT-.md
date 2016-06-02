---
title: View the XML for an Analysis Services Project (SSDT)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
---
# View the XML for an Analysis Services Project (SSDT)
  When you are working with an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database in project mode, [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] creates an XML definition for each object within the project folder. You can view the contents of the XML file for each object within [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. You can also edit the XML file directly; however, this is not recommended in most circumstances as you may make changes that make the XML unreadable by [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
> [!NOTE]  
>  You cannot view the xml code for an entire project, but rather you view the code for each object because a separate file exists for each object. The only way to view the code for an entire project is to build the project and view the ASSL code in the \<project name\>.asdatabase file.  
  
### To view the XML code for an object  
  
1.  Open the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
2.  Right\-click the object in Solution Explorer and then click **View Code**.  
  
     The XML code for the object appears in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
## See Also  
 [Build Analysis Services Projects &#40;SSDT&#41;](../Topic/Build%20Analysis%20Services%20Projects%20\(SSDT\).md)  
  
  