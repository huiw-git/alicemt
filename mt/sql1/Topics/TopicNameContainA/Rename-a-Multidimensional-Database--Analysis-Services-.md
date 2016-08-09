---
title: "Rename a Multidimensional Database (Analysis Services)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
caps.latest.revision: 21
manager: mblythe
---
# Rename a Multidimensional Database (Analysis Services)
The manner in which you change the name of a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database depends upon how you connect to the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database. To change the name of an existing database, you must connect in online mode. To change the name of the database into which objects in an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project will be instantiated, you must connect in project mode.  
  
### To change the database name in online mode  
  
1.  Using [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)], connect directly to the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database.  
  
2.  In Solution Explorer, right-click the database and then click **Edit Database**.  
  
3.  In the **Database name** text box, change the database name.  
  
4.  Click **Save** or **Save All** on the toolbar, click **Save Selected Items** or **Save All** on the **File** menu, or close the **Database Designer** and then click **Save** when prompted.  
  
     The database name is updated in the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance and the database object in Solution Explorer is refreshed.  
  
### To change the database name in project mode  
  
1.  Open the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project.  
  
2.  In Solution Explorer, right-click the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project and then click **Properties**.  
  
3.  In the **Property Pages** dialog box, click **Deployment** in the **Configuration Properties** section.  
  
4.  Change the **Database** property to the new database name.  
  
     The next time the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project is deployed, it will be deployed to this new database name. If this database already exists, it will be overwritten.  
  
### To change the database name using SQL Server Management Studio  
  
-   Right-click the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database and edit the Name property.  
  
## See Also  
 [Server Properties in Analysis Services](../../Topics/TopicNameNotContainA/Server-Properties-in-Analysis-Services.md)   
 [Set Multidimensional Database Properties (Analysis Services)](../../Topics/TopicNameNotContainA/Set-Multidimensional-Database-Properties--Analysis-Services-.md)   
 [Configure Analysis Services Project Properties (SSDT)](../../Topics/TopicNameNotContainA/Configure-Analysis-Services-Project-Properties--SSDT-.md)   
 [Deploy Analysis Services Projects (SSDT)](../../Topics/TopicNameNotContainA/Deploy-Analysis-Services-Projects--SSDT-.md)