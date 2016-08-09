---
title: "Installing R Components without Internet Access"
ms.custom: na
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 9
manager: paulettm
---
# Installing R Components without Internet Access
Setup of the R components used by [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] requires an Internet connection for access to files that are provided either on the Microsoft Download Center or another trusted site. However, you can install these components on a server without Internet access by making local copies as described in this topic.  
  
## Installation on Computers with No Internet Access  
 If you are performing an offline install, [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] cannot access the links for installing required R components. To avoid this problem, you can download a copy of the installers locally and complete setup as described here:  
  
1.  Pause the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup wizard without closing it.  
  
2.  [!INCLUDE[sssNoversion]()] setup should display a dialog box with links to the installers for the required components.  
  
     On opening the link, download begins immediately. By default installers are saved to the **Downloads** folder.  
  
    > [!TIP]  
    >  If a list of links does not appear, you can download the installers from these sites (RC2 and RC3 only).  
    >   
    >  **Microsoft R Open**  
    >   
    >  [http://go.microsoft.com/fwlink/?LinkId=733805&amp;lcid=1033](http://go.microsoft.com/fwlink/?LinkId=733805&amp;lcid=1033)  
    >   
    >  **R Server (Standalone)**  
    >   
    >  [http://go.microsoft.com/fwlink/?LinkId=735050&amp;lcid=1033](http://go.microsoft.com/fwlink/?LinkId=735050&amp;lcid=1033)  
  
3.  Open the installation packages using the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup wizard.  
  
## See Also  
 [Getting Started with SQL Server R Services](../../Topics/TopicNameNotContainA/Getting-Started-with-SQL-Server-R-Services.md)   
 [Troubleshooting R Services Setup](../../Topics/TopicNameNotContainA/Troubleshooting-R-Services-Setup.md)