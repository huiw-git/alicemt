---
title: "View Integration Services Packages in SQL Server Management Studio (SSIS Service)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# View Integration Services Packages in SQL Server Management Studio (SSIS Service)
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] packages. [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)]. Starting in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)], you can manage objects such as packages on the Integration Services server.  
  
 This procedure describes how to connect to [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and view a list of the packages that the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] service manages.  
  
### To connect to Integration Services  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and then click **Connect**.  
  
    > [!IMPORTANT]  
    >  If you cannot connect to [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)], the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] service is likely not running. To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**. In the left pane, click **SQL Server Services**. In the right pane, find the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] service. Start the service if it is not already running.  
  
     [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] opens. By default the Object Explorer window is open and positioned in the lower-left corner of the studio. If Object Explorer is not open, click **Object Explorer** on the **View** menu.  
  
### To view the packages that Integration Services service manages  
  
1.  In Object Explorer, expand the Stored Packages folder.  
  
2.  Expand the Stored Packages subfolders to show packages.  
  
## See Also  
 [Package Management (SSIS Service)](../../Topics/TopicNameNotContainA/Package-Management--SSIS-Service-.md)   
 [Introducing SQL Server Management Studio](assetId:///f289e978-14ca-46ef-9e61-e1fe5fd593be)