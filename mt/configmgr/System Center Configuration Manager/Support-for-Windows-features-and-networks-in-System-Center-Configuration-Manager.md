---
title: "Support for Windows features and networks in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: 8
caps.handback.revision: 0
---
# Support for Windows features and networks in System Center Configuration Manager
This topic identifies [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] support for the following Windows and networking features:  
  
-   [BranchCache](#bkmk_branchcache)  
  
-   [Computers in Workgroups](#bkmk_Workgroups)  
  
-   [DirectAccess](#bkmk_DA)  
  
-   [Data deduplication](#bkmmk_datadedup)  
  
-   [Dual boot computers](#bkmk_dualboot)  
  
-   [Internet protocol version 6](#bkmk_IPv6)  
  
-   [Network Address Translation](#bkmk_NAT)  
  
-   [Specialized storage technology](#bkmk_storage)  
  
##  <a name="bkmk_branchcache"></a> BranchCache  
 Windows BranchCache is integrated in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. You can configure the BranchCache settings on a deployment type for applications, on the deployment for a package, and for task sequences.  
  
 When all the requirements for BranchCache are met, this feature enables clients at remote locations to obtain content from local clients that have a current cache of the content.  
  
 For example, when the first BranchCache-enabled client computer requests content from a distribution point that is configured as a BranchCache server, the client computer downloads and caches the content. This content is then made available for clients on the same subnet that request this same content, and these clients also cache the content. In this manner, successive clients on the same subnet do not have to download content from the distribution point, and the content is distributed across multiple clients for future transfers.  
  
 **To support BranchCache with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:**  
  
-   Add the **Windows BranchCache** feature to the site system server that is configured as a distribution point.  
  
    -   Distribution points on servers configured to support BranchCache require no additional configuration  
  
    -   You cannot add Windows BranchCache to a cloud-based distribution point, but cloud-based distribution points support the download of content by clients that are configured for Windows BranchCache  
  
 **To enable clients to use BranchCache:**  
  
-   The clients that can support BranchCache must be configured for BranchCache distributed mode  
  
-   The operating system setting for BITS client settings must be enabled to support BranchCache  
  
 **The following client operating systems  are supported with Windows BranchCache:**  
  
|Operating system|Support details|  
|----------------------|---------------------|  
|Windows 7 with SP1|Supported by default|  
|Windows 8|Supported by default|  
|Windows 8.1|Supported by default|  
|Windows 10|Supported by default|  
|Windows Server 2008 with SP2|**Requires BITS 4.0**-  You can install the BITS 4.0 release on [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients by using software updates or software distribution. For more information about the BITS 4.0 release, see [Windows Management Framework](http://go.microsoft.com/fwlink/p/?LinkId=181979).<br /><br /> On this operating system, the BranchCache client functionality is not supported for software distribution that is run from the network or for SMB file transfers. Additionally, this operating system cannot use BranchCache functionality with cloud-based distribution points.|  
|Windows Server 2008 R2|Supported by default|  
|Windows Server 2012|Supported by default|  
|Windows Server 2012 R2|Supported by default|  
  
 For more information about BranchCache, see [BranchCache for Windows](http://go.microsoft.com/fwlink/p/?LinkId=177945) in the Windows Server documentation.  
  
##  <a name="bkmk_Workgroups"></a> Computers in Workgroups  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides support for clients in workgroups.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports moving a client from a workgroup to a domain or from a domain to a workgroup. For more information, see [How to Install Configuration Manager Clients on Workgroup Computers](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md#BKMK_ClientWorkgroup) in the [How to deploy clients to Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md) topic.  
  
> [!NOTE]  
>  Although clients in workgroups are supported, all site systems must be members of a supported Active Directory Domain  
  
##  <a name="bkmmk_datadedup"></a> Data deduplication  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the use of data deduplication with distribution points on the following operating systems:  
  
-   Windows Server 2012  
  
-   Windows Server 2012 R2  
  
> [!IMPORTANT]  
>  The volume that hosts package source files cannot be marked for data deduplication. This is because data deduplication uses reparse points and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support using a content source location with files stored on reparse points.  
  
 For more information, see [Configuration Manager Distribution Points and Windows Server 2012 Data Deduplication](http://blogs.technet.com/b/configmgrteam/archive/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication.aspx) on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] team blog, and [Data Deduplication Overview](http://technet.microsoft.com/library/hh831602.aspx) in the Windows Server TechNet library.  
  
##  <a name="bkmk_DA"></a> DirectAccess  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the DirectAccess feature in Windows Server 2008 R2 for communication between site system servers and clients.  
  
-   When all the requirements for DirectAccess are met, by using this feature, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients on the Internet can communicate with their assigned site as if they were on the intranet.  
  
-   For server-initiated actions, such as remote control and client push installation, the initiating computer (such as the site server) must be running IPv6, and this protocol must be supported on all intervening networking devices.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support the following over DirectAccess:  
  
-   Deploying operating systems  
  
-   Communication between [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites  
  
-   Communication between [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system servers within a site  
  
##  <a name="bkmk_dualboot"></a> Dual boot computers  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot manage more than one operating system on a single computer. If there is more than one operating system on a computer that must be managed, adjust the discovery and installation methods that are used to ensure that the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is installed only on the operating system that has to be managed.  
  
##  <a name="bkmk_IPv6"></a> Internet protocol version 6  
 In addition to Internet Protocol version 4 (IPv4), [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports Internet Protocol version 6 (IPv6) with the following exceptions:  
  
|Function|Exception to IPv6 support|  
|--------------|-------------------------------|  
|Cloud-based distribution points|IPv4 is required to support Microsoft Azure and cloud-based distribution points.|  
|Mobile devices that are enrolled by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] and the Microsoft service connector|IPv4 is required to support mobile devices that are enrolled by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] and the Microsoft service connector.|  
|Network Discovery|IPv4 is required when you configure a DHCP server to search in Network Discovery.|  
|Operating system deployment|IPv4 is required to support operating system deployment.|  
|Wake-up proxy communication|IPv4 is required to support the client wake-up proxy packets.|  
|Windows CE|IPv4 is required to support the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on Windows CE devices.|  
  
##  <a name="bkmk_NAT"></a> Network Address Translation  
 Network Address Translation (NAT) is not supported in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], unless the site supports clients that are on the Internet and the client detects that it is connected to the Internet. For more information about Internet-based client management, see [Plan for managing Internet-based clients in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-managing-Internet-based-clients-in-System-Center-Configuration-Manager.md).  
  
##  <a name="bkmk_storage"></a> Specialized storage technology  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] works with any hardware that is certified on the Windows Hardware Compatibility List for the version of the operating system that the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] component is installed on. Site Server roles require NTFS file systems so that directory and file permissions can be set. Because [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] assumes that it has complete ownership of a logical drive, site systems that run on separate computers cannot share a logical partition on any storage technology. However, each computer can use a separate logical partition on the same physical partition of a shared storage device.  
  
 **Support considerations:**  
  
-   **Storage Area Network**: A Storage Area Network (SAN) is supported when a supported Windows-based server is attached directly to the volume that is hosted by the SAN.  
  
-   **Single Instance Storage**: [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support configuration of distribution point package and signature folders on a Single Instance Storage (SIS)-enabled volume.  
  
     Additionally, the cache of a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is not supported on a SIS-enabled volume.  
  
-   **Removable Disk Drive**: [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support install of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system or clients on a removable disk drive.  
  
## See Also  
 [Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md)