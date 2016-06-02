---
title: Installing R Components without Internet Access
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
---
# Installing R Components without Internet Access
  Setup of the R components used by [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] requires an Internet connection for access to files that are provided either on the Microsoft Download Center or another trusted site. However, you can install these components on a server without Internet access by making local copies as described in this topic.  
  
## Installation on Computers with No Internet Access  
 If you are performing an offline install, [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] cannot access the links for installing required R components. To avoid this problem, you can download a copy of the installers locally and complete setup as described here:  
  
1.  Pause the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup wizard without closing it.  
  
2.  Setup should display a dialog box with links to the installers for the required components.  
  
     On opening the link, download begins immediately. By default installers are saved to the **Downloads** folder.  
  
    > [!TIP]  
    >  If the links are not displayed, you can download the installers from these sites:  
    >   
    >  **Microsoft R**  
    >   
    >  [SRS_8.0.2.0_1033.cab](http://go.microsoft.com/fwlink/?LinkId=733805&amp;lcid=1033)  
    >   
      
  
3.  Open the installation packages using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup wizard.  
  
## See Also  
 [Getting Started with SQL Server R Services](../../Topics\TopicNameNotContainA/Getting-Started-with-SQL-Server-R-Services.md)   
 [Troubleshooting R Services Setup](../../Topics\TopicNameNotContainA/Troubleshooting-R-Services-Setup.md)  
  
  