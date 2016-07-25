---
title: "Create a Multiserver Environment"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
caps.latest.revision: 5
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Create a Multiserver Environment
Multiserver administration requires that you set up a master server (MSX) and one or more target servers (TSX). Jobs that will be processed on all the target servers are first defined on the master server and then downloaded to the target servers.  
  
By default, full Secure Sockets Layer (SSL) encryption and certificate validation are enabled for connections between master servers and target servers. For more information, see [Set Encryption Options on Target Servers](../content/Set-Encryption-Options-on-Target-Servers.md).  
  
If you have a large number of target servers, avoid defining your master server on a production server that has significant performance requirements from other [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] functionality, because target server traffic can slow performance on your production server. If you also forward events to a dedicated master server, you can centralize administration on one server. For more information, see [Manage Events](../content/Manage-Events.md).  
  
> [!NOTE]  
> To use multiserver job processing, the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service account must be a member of the **msdb** database role **TargetServersRole** on the master server. The Master Server Wizard automatically adds the service account to this role as part of the enlistment process  
  
## Considerations for Multiserver Environments  
See the table below for supported MSX/TSX configurations.  
  
||**TSX = 7.0**|**TSX = 8.0 < SP3**|**TSX = 8.0 SP3 or higher**|**TSX = 9.0**|**TSX= 10.0**|**TSX = 10.5**|**TSX = 11.0**|  
|-|------------------|------------------------|--------------------------------|------------------|------------------|-------------------|-------------------|  
|**MSX = 7.0**|Yes|Yes|No|No|No|No|No|  
|**MSX = 8.0 < SP3**|Yes|Yes|No|No|No|No|No|  
|**MSX = 8.0 SP3 or higher**|No|No|Yes|Yes|Yes|Yes|Yes|  
|**MSX = 9.0**|No|No|No|Yes|Yes|Yes|Yes|  
|**MSX = 10.0**|No|No|No|No|Yes|Yes|Yes|  
|**MSX = 10.5**|No|No|No|No|No|Yes|Yes|  
|**MSX = 11.0**|No|No|No|No|No|No|Yes|  
  
Consider the following issues when creating a multiserver environment:  
  
-   Each target server reports to only one master server. You must defect a target server from one master server before you can enlist it into a different one.  
  
-   When changing the name of a target server, you must defect it before changing the name and re-enlist it after the change.  
  
-   If you want to dismantle a multiserver configuration, you must defect all the target servers from the master server.  
  
-   SQL Server Integration Services only supports target servers that are the same version or higher than the master server version.  
  
## Related Tasks  
The following topics document common tasks for creating a multiserver environment.  
  
|Description|Topic|  
|---------------|---------|  
|Describes how to create a master server.|[Make a Master Server](../content/Make-a-Master-Server.md)|  
|Describes how to create a target server.|[Make a Target Server](../content/Make-a-Target-Server.md)|  
|Describes how to enlist a target server into a master server.|[Enlist a Target Server to a Master Server](../content/Enlist-a-Target-Server-to-a-Master-Server.md)|  
|Describes how to defect a target server from a master server.|[Defect a Target Server from a Master Server](../content/Defect-a-Target-Server-from-a-Master-Server.md)|  
|Describes how to defect multiple target servers from a master server.|[Defect Multiple Target Servers from a Master Server](../content/Defect-Multiple-Target-Servers-from-a-Master-Server.md)|  
|Describes how to check the status of a target server.|[sp_help_targetserver (Transact-SQL)](assetId:///f841d3bd-901a-4980-ad0b-1c6eeba3f717)<br /><br />[sp_help_targetservergroup (Transact-SQL)](assetId:///ec3a4a68-b591-431c-9518-053ede522d0c)|  
  
## See Also  
[Troubleshoot Multiserver Jobs That Use Proxies](../content/Troubleshoot-Multiserver-Jobs-That-Use-Proxies.md)  
  
