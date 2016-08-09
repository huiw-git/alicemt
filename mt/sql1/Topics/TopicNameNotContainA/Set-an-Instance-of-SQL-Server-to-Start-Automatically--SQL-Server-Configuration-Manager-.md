---
title: "Set an Instance of SQL Server to Start Automatically (SQL Server Configuration Manager)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-01-06
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# Set an Instance of SQL Server to Start Automatically (SQL Server Configuration Manager)
This topic describes how to set an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to start automatically in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using SQL Server Configuration Manager. During setup, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is normally configured to start automatically. If this was not done, you can change that setting at any time.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To set an instance of SQL Server to start automatically  
  
1.  On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Topics/TopicNameContainA/tokens/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
    > [!NOTE]  
    >  Because [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager does not appear as an application in newer versions of Windows.  
    >   
    >  -   **Windows 10**:  
    >          To open [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager13.msc (for [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]). For previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] replace 13 with a smaller number. Clicking SQLServerManager13.msc opens the Configuration Manager. To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager13.msc, and then click **Open file location**. In the Windows File Explorer, right-click SQLServerManager13.msc, and then click **Pin to Start** or **Pin to taskbar**.  
    > -   **Windows 8**:  
    >          To open [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager<version\>.msc** such as **SQLServerManager13.msc**, and then press **Enter**.  
  
2.  In **SQL Server Configuration Manager**, expand **Services**, and then click **SQL Server**.  
  
3.  In the details pane, right-click the name of the instance you want to start automatically, and then click **Properties**.  
  
4.  In the **SQL Server <***instancename***> Properties** dialog box, set **Start Mode** to **Automatic**.  
  
5.  Click **OK**, and then close [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager.  
  
## See Also  
 [Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Prevent-Automatic-Startup-of-an-Instance-of-SQL-Server--SQL-Server-Configuration-Manager-.md)   
 [Connect to Another Computer (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Connect-to-Another-Computer--SQL-Server-Configuration-Manager-.md)   
 [How to: Configure WMI to Show Server Status in SQL Server Tools](assetId:///7e97197b-ed4d-40d1-9a52-9ab1d92401d7)