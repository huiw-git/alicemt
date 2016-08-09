---
title: "Associate a Master Data Services Database and Web Application"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Associate a Master Data Services Database and Web Application
Associate your [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application with a [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database to specify the database to use for web operations.  
  
## Prerequisites  
  
-   [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)] must be installed on the local computer. For more information, see [Install Master Data Services](../../Topics/TopicNameNotContainA/Install-Master-Data-Services.md).  
  
-   A local [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application must exist. For more information, see [Create a Master Data Manager Web Application (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Master-Data-Manager-Web-Application--Master-Data-Services-.md).  
  
-   Either a local or remote [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database must exist. For more information, see [Create a Master Data Services Database](../../Topics/TopicNameContainA/Create-a-Master-Data-Services-Database.md).  
  
### To associate a Master Data Services database and web application  
  
1.  Open [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)].  
  
2.  In the left pane, click **Web Configuration**.  
  
3.  On the **Web Configuration** page, under **Web application**, from the **Website** list, select the website that contains your [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application.  
  
4.  In the **Web application** box, select the web application that hosts [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)].  
  
5.  Under **Associate Application with Database**, click **Select**. The **Connect to Database** dialog box opens.  
  
6.  Specify connection information for the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that hosts the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database, and click **Connect**.  
  
7.  From the **Master Data Services database** list, select the database you want to associate the web application with and then click **OK**.  
  
8.  Under **Associate Application with Database**, verify that the instance and database information are correct, and then click **Apply**.  
  
## Next Steps  
  
-   Programmatic access to [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] web services is automatically enabled when the web application is created. To let developers access the service metadata to easily generate proxy classes for programmatic access, enable metadata publishing. For more information, see [Create Master Data Manager Web Service Proxy Classes](assetId:///8bdab026-a0c0-41f3-9d36-f3919c23247f).  
  
-   Add users and groups to [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)]. If no users or groups have been granted access to [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], you must open [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] using the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] system administrator credentials. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md) and [Users and Groups (Master Data Services)](../../Topics/TopicNameNotContainA/Users-and-Groups--Master-Data-Services-.md).  
  
## See Also  
 [Install Master Data Services](../../Topics/TopicNameNotContainA/Install-Master-Data-Services.md)   
 [Web Configuration Page (Master Data Services Configuration Manager)](../../Topics/TopicNameNotContainA/Web-Configuration-Page--Master-Data-Services-Configuration-Manager-.md)