---
title: "Connect in Online Mode to an Analysis Services Database"
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
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
caps.latest.revision: 14
caps.handback.revision: 0
manager: mblythe
---
# Connect in Online Mode to an Analysis Services Database
You can connect directly to an existing [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database and directly modify objects within that database. When you connect directly to an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database, changes to objects occur immediately and no [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project is created within [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].  
  
### To Connect Directly to an Analysis Services Database by using SQL Server Data Tools  
  
1.  Open [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].  
  
2.  On the **File** menu, point to **Open** and then click **Analysis Services Database**.  
  
3.  Select **Connect to existing database**.  
  
4.  Specify the server name and the database name.  
  
     You can either type the database name or query the server to view the existing databases on the server.  
  
5.  Click **OK**.  
  
     You can now directly edit any objects within the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database.  
  
## See Also  
 [Working with Analysis Services Projects and Databases During the Development Phase](../../Topics/TopicNameNotContainA/Working-with-Analysis-Services-Projects-and-Databases-During-the-Development-Phase.md)   
 [Creating Multidimensional Models Using SQL Server Data Tools (SSDT)](../../Topics/TopicNameNotContainA/Creating-Multidimensional-Models-Using-SQL-Server-Data-Tools--SSDT-.md)