---
title: "Install and Uninstall OData Source Component"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
caps.latest.revision: 8
manager: jhubbard
robots: noindex,nofollow
---
# Install and Uninstall OData Source Component
This topic provides instructions for installing or removing OData Source Component on your computer.  
  
## Installation  
 The OData Source Component requires following prerequisite components to be installed on your computer.  
  
-   SQL Server Data Tools (to design packages)  
  
-   SQL Server Integration Services (to run packages outside Visual Studio)  
  
 To install the OData Source Component, download [SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkId=391999) and run one of the following MSI files.  
  
-   ODataSourceForSQLServer2014-amd64.msi for 64bit platforms  
  
-   ODataSourceForSQLServer2014-x86.msi for 32bit platforms  
  
> [!IMPORTANT]  
>  The 64bit installer will install both 32bit and 64bit versions of the OData Source Component. You only need to run the 32bit installer if you are using a 32bit OS.  
  
## Uninstallation  
 The OData Source component can be uninstalled from the **Programs and Features** menu. Find the **Microsoft SQL Server SSIS OData Source Component (x64)** entry and click **Uninstall**.