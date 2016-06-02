---
title: Install SQL Server Database Engine
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
---
# Install SQL Server Database Engine
  The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] component of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is the core service for storing, processing, and securing data. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications in your enterprise.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports up to 50 instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] on a single computer. To create a typical [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation, see [Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md).  
  
 **Important** For local installations, you must run Setup as an administrator. If you install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.  
  
 The following features are installed when you select **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Database Engine** on the Components to Install page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard:  
  
-   [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]  
  
-   Replication \- is an optional component  
  
-   Full\-Text Search \- is an optional component  
  
-   Data Quality Services – is an optional component  
  
    > [!NOTE]  
    >  In this release, selecting the **Data Quality Services** check box in setup does not install the Data Quality Services \(DQS\) server. You will have to perform additional steps post installation to install DQS server. For more information, see [Install Data Quality Services](../../Topics\TopicNameNotContainA/Install-Data-Quality-Services.md).  
  
 The following additional features are options for many typical user scenarios:  
  
-   Data Quality Client  
  
-   [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]  
  
-   Connectivity components  
  
-   Programming models  
  
-   Management tools  
  
-   [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]  
  
-   Documentation components  
  
> [!NOTE]  
>  By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. To install sample databases and sample code, see the [CodePlex Web site](http://go.microsoft.com/fwlink/?LinkId=87843).  
  
## See Also  
 [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)   
 [Editions and Components of SQL Server 2016](../../Topics\TopicNameNotContainA/Editions-and-Components-of-SQL-Server-2016.md)   
 [Planning a SQL Server Installation](../../Topics\TopicNameContainA/Planning-a-SQL-Server-Installation.md)   
 [High Availability Solutions &#40;SQL Server&#41;](../Topic/High%20Availability%20Solutions%20\(SQL%20Server\).md)   
 [Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md)  
  
  