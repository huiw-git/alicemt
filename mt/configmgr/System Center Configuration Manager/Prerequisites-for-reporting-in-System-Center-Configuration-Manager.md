---
title: "Prerequisites for reporting in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 9cc508a5-5023-4833-b776-ae9a6971138f
caps.latest.revision: 5
caps.handback.revision: 0
---
# Prerequisites for reporting in System Center Configuration Manager
Reporting in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] has external dependencies and dependencies within the product.  
  
## Dependencies external to Configuration Manager  
 The following table lists the external dependencies for reporting.  
  
|Prerequisite|More information|  
|------------------|----------------------|  
|SQL Server Reporting Services|Before you can use reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you must install and configure SQL Server Reporting Services.<br /><br /> For information about planning and deploying Reporting Services in your environment, see the [Reporting Services](http://go.microsoft.com/fwlink/p/?LinkId=212032) section in the SQL Server 2008 Books Online.|  
|Site system role dependencies for the computers that run the reporting services point.|[Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md)|  
  
## Dependencies internal to Configuration Manager  
 The following table lists the dependencies for reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
|Prerequisite|More information|  
|------------------|----------------------|  
|Reporting services point|The reporting services point site system role must be configured before you can use reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For more information about how to install and configure a reporting services point, see [Configuring reporting in System Center Configuration Manager](../System Center Configuration Manager/Configuring-reporting-in-System-Center-Configuration-Manager.md).|  
  
## Supported SQL Server versions for the Reporting Services Point  
 The Reporting Services database can be installed on either the default instance or a named instance of a 64-bit SQL Server installation. The SQL Server instance can be co-located with the site system server, or on a remote computer.  
  
 The following table lists the SQL Server versions that are supported by the reporting services point.  
  
|SQL Server version|Reporting Services point|  
|------------------------|------------------------------|  
|SQL Server 2008 SP2 with a minimum of cumulative update 9<br /><br /> -   Standard<br />-   Enterprise<br />-   Datacenter|√|  
|SQL Server 2008 SP3 with a minimum of cumulative update 4<br /><br /> -   Standard<br />-   Enterprise<br />-   Datacenter|√|  
|SQL Server 2008 R2 with SP1 and with a minimum of cumulative update 6<br /><br /> -   Standard<br />-   Enterprise<br />-   Datacenter|√|  
|SQL Server 2008 R2 with SP2<br /><br /> -   Standard<br />-   Enterprise<br />-   Datacenter|√|  
|SQL Server Express 2008 R2 with SP1 and with a minimum of cumulative update 4|Not Supported|  
|SQL Server Express 2008 R2 with SP2|Not Supported|  
|SQL Server 2012 and with a minimum of cumulative update 2<br /><br /> -   Standard<br />-   Enterprise|√|  
|SQL Server 2012 with SP1 and no minimum cumulative update<br /><br /> -   Standard<br />-   Enterprise|√|  
|SQL Server 2014<br /><br /> -   Standard<br />-   Enterprise|√|  
  
## See Also  
 [Planning for reporting in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-reporting-in-System-Center-Configuration-Manager.md)