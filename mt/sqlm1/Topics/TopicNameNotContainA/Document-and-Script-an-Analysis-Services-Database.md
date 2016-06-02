---
title: Document and Script an Analysis Services Database
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
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
---
# Document and Script an Analysis Services Database
  After an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to output the metadata of the database, or of an object contained in the database, as an XML for Analysis \(XMLA\) script. You can output this script to a new **XMLA Query Editor** window, to a file, or to the Clipboard. For more information about XMLA, see [Analysis Services Scripting Language &#40;ASSL for XMLA&#41;](../Topic/Analysis%20Services%20Scripting%20Language%20\(ASSL%20for%20XMLA\).md).  
  
 The generated XMLA script uses [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Scripting Language \(ASSL\) elements to define the objects contained by the script. If you generated a CREATE script, the resulting XMLA script contains an XMLA **Create** command and ASSL elements that can be used to create the entire [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database structure on an instance. If you generated an ALTER script, the resulting XMLA script contains an XMLA **Alter** command and ASSL elements that can be used to restore the structure of an existing [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database to the state of the database at the time the script was created.  
  
 You can use the generated XMLA script from an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database in many ways, including:  
  
-   To maintain a backup script that allows you to recreate all the database objects and permissions.  
  
-   To create or update database development code.  
  
-   To create a test or development environment from an existing schema.  
  
## See Also  
 [Modify or Delete an Analysis Services Database](../../Topics\TopicNameNotContainA/Modify-or-Delete-an-Analysis-Services-Database.md)   
 [Alter Element &#40;XMLA&#41;](../Topic/Alter%20Element%20\(XMLA\).md)   
 [Create Element &#40;XMLA&#41;](../Topic/Create%20Element%20\(XMLA\).md)  
  
  