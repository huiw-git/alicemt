---
title: Uninstall and Remove Master Data Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: efc2431c-588b-42e7-b23b-c875145a33f6
---
# Uninstall and Remove Master Data Services
  To uninstall the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] feature from an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], follow the steps in [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../Topic/Uninstall%20an%20Existing%20Instance%20of%20SQL%20Server%20\(Setup\).md) and specify [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] as a feature to remove on the **Select Features** page. The uninstall process removes [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] folders and files, and uninstalls [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] from the local computer.  
  
 To prevent data loss and avoid affecting other computers in the system, some items are not removed or changed by the uninstall process. Review the following table to determine whether to leave or remove items.  
  
|Item|Description|  
|----------|-----------------|  
|Folders and files|The uninstall process removes most folders and files from the installation path.<br /><br /> The uninstall process does not remove the Master Data Services and MDSTempDir folders from the installation location. After the uninstall process is complete, you can manually delete these folders from the file system. For more information, see [Folder and File Permissions &#40;Master Data Services&#41;](../Topic/Folder%20and%20File%20Permissions%20\(Master%20Data%20Services\).md).|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] assemblies|The uninstall process removes [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] assemblies from the Global Assembly Cache \(GAC\).|  
|Database|The uninstall process does not affect the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. The database remains intact in the instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] so that you do not lose any data, including master data, model objects, user and group permissions, business rules, and so on.<br /><br /> If you do not need the database, and do not anticipate connecting it to another [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] web site or application in the future, you might want to delete the database from the instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] that hosts it. For more information, see [Delete a Database](../../Topics\TopicNameContainA/Delete-a-Database.md).|  
|[!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] and Web.config|The uninstall process removes the WebApplication folder from the file system. The WebApplication folder contains the web application files and Web.config file for [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].<br /><br /> **\*\* Important \*\*** Before you uninstall, you might want to copy the Web.config file to another location to preserve any custom settings or other information in the file. After the uninstall process completes, the Web.config file is not recoverable.|  
|Internet Information Services \(IIS\) items|The uninstall process does not affect any application pools, web sites, or web applications in IIS on the local computer. Because the uninstall process removes the WebApplication folder and Web.config file for [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], any [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web applications that require those files will no longer serve content. If users try to access the web application, they will receive HTTP Error 500.19\-Internal Server Error: "The requested page cannot be accessed because the related configuration data for the page is invalid."<br /><br /> If you no longer require the web site or application, and the application pool serving your site or application, you can use an IIS tool to delete them. For more information, see [IIS 7 Operations Guide](http://go.microsoft.com/fwlink/?LinkId=184885) on [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] TechNet.|  
|**MDS\_ServiceAccounts** group|After the uninstall process is complete, the **MDS\_ServiceAccounts** Windows group and any service accounts added to the group remain. If you no longer need the group and accounts, you can remove them.|  
|Registry|The uninstall process removes all [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] registry keys from the Windows registry.|  
  
## See Also  
 [Install Master Data Services](../../Topics\TopicNameNotContainA/Install-Master-Data-Services.md)  
  
  