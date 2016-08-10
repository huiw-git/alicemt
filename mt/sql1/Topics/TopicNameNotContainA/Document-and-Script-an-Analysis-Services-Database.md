---
title: "Document and Script an Analysis Services Database"
ms.custom: na
ms.date: 08/09/2016
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
caps.latest.revision: 36
manager: mblythe
---
# Document and Script an Analysis Services Database
After an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to output the metadata of the database, or of an object contained in the database, as an XML for Analysis (XMLA) script. You can output this script to a new **XMLA Query Editor** window, to a file, or to the Clipboard. For more information about XMLA, see [Analysis Services Scripting Language (ASSL)-deleted](assetId:///ca0e852e-9002-4224-a0f0-bd96f2fc5c65).  
  
 The generated XMLA script uses [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] Scripting Language (ASSL) elements to define the objects contained by the script. If you generated a CREATE script, the resulting XMLA script contains an XMLA **Create** command and ASSL elements that can be used to create the entire [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database structure on an instance. If you generated an ALTER script, the resulting XMLA script contains an XMLA **Alter** command and ASSL elements that can be used to restore the structure of an existing [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database to the state of the database at the time the script was created.  
  
 You can use the generated XMLA script from an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database in many ways, including:  
  
-   To maintain a backup script that allows you to recreate all the database objects and permissions.  
  
-   To create or update database development code.  
  
-   To create a test or development environment from an existing schema.  
  
## See Also  
 [Modify or Delete an Analysis Services Database](../../Topics/TopicNameNotContainA/Modify-or-Delete-an-Analysis-Services-Database.md)   
 [Alter Element (XMLA)](assetId:///84e58385-c9ba-48fa-a867-94d35b777a56)   
 [Create Element (XMLA)](assetId:///a623d362-a1ac-40e4-8816-65fac89cb391)