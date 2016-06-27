---
title: What&#39;s new in Hyper-V on Windows Server 2016 Technical Preview
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - techgroup-compute
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a65a98e-54b6-4c41-9732-1e3d32fe3a5f
---
# What&#39;s new in Hyper-V on Windows Server 2016 Technical Preview
**This is preliminary content and subject to change.**  
  
This article explains the new and changed functionality of Hyper\-V on [!INCLUDE[winthreshold_server_1](../../compute/hyper-v/includes/winthreshold_server_1_md.md)] and [!INCLUDE[winthreshold_mshvs_1](../../compute/hyper-v/includes/winthreshold_mshvs_1_md.md)]. To use new features on virtual machines created with Windows Server 2012 R2 and moved or imported to a server that runs Hyper\-V on [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)], you'll need to manually upgrade the virtual machine configuration version. For instructions, see [Upgrade virtual machine version](Upgrade%20virtual%20machine%20version%20in%20Hyper-V%20on%20Windows%2010%20or%20Windows%20Server%202016.md).  
 
 If you're new to Hyper-V and want to learn more about it, see the [Hyper-V Technology Overview](Hyper-V%20Technology%20Overview.md).
  
Here's what's included in this article and whether the functionality is new or updated.  
  
|Feature or Functionality|New or Updated|  
|--------|-------|  
|[Compatible with Connected Standby](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md#BKMK_standby) | New |  
|[Discrete device assignment](#BKMK_device)| New |  
|[Host resource protection](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md#BKMK_host)| New|  
|[Hot add and remove for network adapters and memory](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md#BKMK_hot)| New|  
|[Hyper-V Manager improvements](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md#BKMK_Mgmt)| Updated|  
|[Integration services delivered through Windows Update](#BKMK_IS)| Updated|  
|[Linux Secure Boot](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md#BKMK_linux)| New|  
|[Nested virtualization](#BKMK_nested)| New|  
|[Networking features](#BKMK_networking)| New|  
|[Production checkpoints](#BKMK_check)| New|  
|[Rolling Hyper-V Cluster Upgrade](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md#BKMK_HyperVRollingUpgrades)| New|
|[Shared virtual hard disks](#BKMK_shared) | Updated|
|[Start order priority for clustered virtual machines](#BKMK_StartOrder)| New|  
|[Storage quality of service (QoS)](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md#BKMK_QoS)| Updated|  
| [Shielded virtual machines](#BKMK_shielded)| New|  
| [Virtual machine configuration file format](#BKMK_Config)| Updated|  
| [Virtual machine configuration version](#BKMK_ConfgVersion)| Updated|  
| [Windows Containers](#BKMK_Containers)| New|  
| [Windows PowerShell Direct](#BKMK_PowerShellDirect)| New|  
  
## <a name="BKMK_standby"></a>Compatible with Connected Standby  
When the Hyper\-V role is installed on a computer that uses the Always On\/Always Connected \(AOAC\) power model, the **Connected Standby** power state is now available.  
  
## <a name="BKMK_device"></a>Discrete device assignment  
This feature lets you give a virtual machine direct and exclusive access to some PCIe hardware devices. Using a device in this way bypasses the Hyper\-V virtualization stack, which results in faster access. For details on supported hardware, see  "Discrete device assignment" in [System requirements for Hyper-V on Windows Server 2016 Technical Preview](../../compute/hyper-v/System-requirements-for-Hyper-V-on-Windows-Server-2016-Technical-Preview.md). For details, including how to use this feature and considerations, see the post "[Discrete Device Assignment -- Description and background](http://blogs.technet.com/b/virtualization/archive/2015/11/19/discrete-device-assignment.aspx)" in the Virtualization blog.  
  
## <a name="BKMK_host"></a>Host resource protection  
This feature helps prevent a virtual machine from using more than its share of system resources by looking for excessive levels of activity. This can help prevent a virtual machine's excessive activity from degrading the performance of the host or other virtual machines. When monitoring detects a virtual machine with excessive activity, the virtual machine is given fewer resources. This monitoring and enforcement is off by default. Use Windows PowerShell to turn it on or off. To turn it on, run this command:  
  
```  
Set-VMProcessor -EnableHostResourceProtection $true  
```       
  
## <a name="BKMK_hot"></a>Hot add and remove for network adapters and memory  
You can now add or remove a network adapter while the virtual machine is running, without incurring downtime. This works for generation 2 virtual machines that run either Windows or Linux operating systems.  
  
You can also adjust the amount of memory assigned to a virtual machine while it's running, even if you haven’t enabled Dynamic Memory. This works for both generation 1 and generation 2 virtual machines, running [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] or [!INCLUDE[winthreshold_client_2](../../compute/hyper-v/includes/winthreshold_client_2_md.md)].  
  
## <a name="BKMK_Mgmt"></a>Hyper\-V Manager improvements  
  
-   **Alternate credentials support** – You can now use a different set of credentials in Hyper\-V Manager when you connect to another [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] or [!INCLUDE[winthreshold_client_2](../../compute/hyper-v/includes/winthreshold_client_2_md.md)] remote host. You can also save these credentials to make it easier to log on again.  
  
-   **Manage earlier versions** – With Hyper\-V Manager in [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] and [!INCLUDE[winthreshold_client_2](../../compute/hyper-v/includes/winthreshold_client_2_md.md)], you can manage computers running Hyper\-V on [!INCLUDE[win8_server_2](../../compute/hyper-v/includes/win8_server_2_md.md)], [!INCLUDE[win8_client_2](../../compute/hyper-v/includes/win8_client_2_md.md)], [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)] and [!INCLUDE[winblue_client_2](../../compute/hyper-v/includes/winblue_client_2_md.md)].  
  
-   **Updated management protocol** – Hyper\-V Manager has been updated to communicate with remote Hyper\-V hosts using the WS\-MAN protocol, which permits CredSSP, Kerberos or NTLM authentication. When you use CredSSP to connect to a remote Hyper\-V host, you can do a live migration without enabling constrained delegation in Active Directory. The WS\-MAN\-based infrastructure also makes it easier to enable a host for remote management. WS\-MAN connects over port 80, which is open by default.  
  
## <a name="BKMK_IS"></a>Integration services delivered through Windows Update  
Updates to integration services for Windows guests are distributed through Windows Update. For service providers and private cloud hosters, this puts the control of applying updates into the hands of the tenants who own the virtual machines. Tenants can now update their Windows virtual machines with all updates, including the integration services, using a single method. For details about integration services for Linux guests, see [Linux and FreeBSD Virtual Machines on Hyper-V](../Topic/Supported%20Linux%20and%20FreeBSD%20virtual%20machines%20for%20Hyper-V%20on%20Windows.md).  
  
> [!IMPORTANT]  
> The vmguest.iso image file is no longer needed, so it isn't included with Hyper\-V on [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)].  
  
## <a name="BKMK_linux"></a>Linux Secure Boot  
Linux operating systems running on generation 2 virtual machines can now boot with the Secure Boot option enabled. Ubuntu 14.04 and later, SUSE Linux Enterprise Server 12 and later, Red Hat Enterprise Linux 7.0 and later, and CentOS 7.0 and later are enabled for Secure Boot on hosts that run [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)]. Before you boot the virtual machine for the first time, you must configure the virtual machine to use the Microsoft UEFI Certificate Authority. You can do this from Hyper\-V Manager, Virtual Machine Manager, or an elevated Windows Powershell session. For Windows PowerShell, run this command:  
  
```  
Set-VMFirmware vmname -SecureBootTemplate MicrosoftUEFICertificateAuthority  
```  
  
For more information about Linux virtual machines on Hyper\-V, see [Linux and FreeBSD Virtual Machines on Hyper-V](../Topic/Supported%20Linux%20and%20FreeBSD%20virtual%20machines%20for%20Hyper-V%20on%20Windows.md).  
  
## <a name="BKMK_nested"></a>Nested virtualization  
This feature lets you use a virtual machine as a Hyper\-V host and create virtual machines within that virtualized host. This can be especially useful for development and test environments. To use nested virtualization, you'll need:  
  
-   At least 4 GB RAM available for the virtualized Hyper\-V host.  
  
-   To run at least [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] 4 or [!INCLUDE[winthreshold_client_2](../../compute/hyper-v/includes/winthreshold_client_2_md.md)] build 10565 on both the physical Hyper\-V host and the virtualized host. Running the same build in both the physical and virtualized environments generally improves performance.  
  
-   A processor with Intel VT\-x \(nested virtualization is available only for Intel processors at this time\).  
  
For details and instructions, see [Nested Virtualization](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/nesting).  
  
## <a name="BKMK_networking"></a>Networking features  
New networking features include:  
  
-   **Remote direct memory access \(RDMA\) and switch embedded teaming \(SET\)**. You can set up RDMA on network adapters bound to a Hyper\-V virtual switch, regardless of whether SET is also used. SET provides a virtual switch with some of same capabilities as NIC teaming. For details, see [Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET)](../Topic/Software%20Defined%20Networking%20(SDN).md#bkmk_rdma).  
  
-   **Virtual machine multi queues \(VMMQ\)**. Improves on VMQ throughput by allocating multiple hardware queues per virtual machine.  The default queue becomes a set of queues for a virtual machine, and traffic is spread between the queues.  
  
-   **Quality of service \(QoS\) for software\-defined networks**. Manages the default class of traffic through the virtual switch within the default class bandwidth.  
  
For more about new networking features, see [What's New in Networking](What's%20New%20in%20Networking.md).  
  
## <a name="BKMK_check"></a>Production checkpoints  
Production checkpoints are “point-in-time” images of a virtual machine. These give you a way to apply a checkpoint that complies with support policies when a virtual machine runs a production workload. Production checkpoints are based on backup technology inside the guest instead of a saved state. For Windows virtual machines, the Volume Snapshot Service \(VSS\) is used. For Linux virtual machines, the file system buffers are flushed to create a checkpoint that's consistent with the file system. If you'd rather use checkpoints based on saved states, choose standard checkpoints instead. For details, see [Choose between standard or production checkpoints](https://technet.microsoft.com/library/dn872510.aspx).  
  
> [!IMPORTANT]  
> New virtual machines use production checkpoints as the default.  
  
## <a name="BKMK_HyperVRollingUpgrades"></a>Rolling Hyper\-V Cluster upgrade  
You can now add a node running [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] to a Hyper\-V Cluster with nodes running [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)]. This allows you to upgrade the cluster without downtime. The cluster runs at a [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)] feature level until you upgrade all nodes in the cluster and update the cluster functional level with the [!INCLUDE[wps_2](../../compute/hyper-v/includes/wps_2_md.md)] cmdlet, [Update\-ClusterFunctionalLevel](https://technet.microsoft.com/library/mt589702.aspx).  
  
> [!IMPORTANT]  
> After you update the cluster functional level, you can't return it to [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)].  
  
For a Hyper-V cluster with a functional level of [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)] with nodes running [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)] and [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)], note the following:  
  
-   Manage the cluster, Hyper\-V, and virtual machines from a node running [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] or [!INCLUDE[winthreshold_client_2](../../compute/hyper-v/includes/winthreshold_client_2_md.md)].  
  
-	You can move virtual machines between all of the nodes in the Hyper\-V cluster.  
  
-   To use new Hyper\-V features, all nodes must run [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] and the cluster functional level must be updated.  
  
-   The virtual machine configuration version for existing virtual machines isn't upgraded. You can upgrade the configuration version only after you upgrade the cluster functional level.  
  
-   Virtual machines that you create are compatible with [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)], virtual machine configuration level 5.  
  
After you update the cluster functional level:  
  
-   You can enable new Hyper\-V features.  
  
-   To make new virtual machine features available, use the Update\-VmConfigurationVersion cmdlet to manually update the virtual machine configuration level. For instructions, see [Upgrade virtual machine version](Upgrade%20virtual%20machine%20version%20in%20Hyper-V%20on%20Windows%2010%20or%20Windows%20Server%202016.md).  
  
-   You can't add a node to the Hyper\-V Cluster that runs [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)].  
  
> [!NOTE]  
> Hyper\-V on [!INCLUDE[winthreshold_client_2](../../compute/hyper-v/includes/winthreshold_client_2_md.md)] doesn't support failover clustering.  
  
For details and instructions, see the [Cluster Operating System Rolling Upgrade](https://technet.microsoft.com/library/dn850430.aspx).  

## <a name="BKMK_shared"></a>Shared virtual hard disks
You can now resize shared virtual hard disks (.vhdx files) used for guest clustering, without downtime. Shared virtual hard disks can be grown or shrunk while the virtual machine is online. Guest clusters can now also protect shared virtual hard disks by using Hyper-V Replica for disaster recovery.
  
## <a name="BKMK_shielded"></a>Shielded virtual machines  
Shielded virtual machines use several features to make it harder for Hyper-V administrators and malware on the host to inspect, tamper with, or steal data from the state of a shielded virtual machine.  Data and state is encrypted, Hyper\-V administrators can't see the video output and disks,  and the virtual machines can be restricted to run only on known, healthy hosts, as determined by a Host Guardian Server. For details, see [Guarded Fabric and Shielded VMs](http://go.microsoft.com/fwlink/?LinkId=746381).  
  
>[!NOTE]  
> As of Technical Preview 5, shielded virtual machines are compatible with Hyper-V Replica. To replicate a shielded virtual machine, the host you want to replicate to must be authorized to run that shielded virtual machine.  
  
## <a name="BKMK_StartOrder"></a>Start order priority for clustered virtual machines  
This feature gives you more control over which clustered virtual machines are started or restarted first. This makes it easier to start virtual machines that provide services before virtual machines that use those services. Define sets, place virtual machines in sets, and specify dependencies. Use Windows PowerShell cmdlets to manage the sets, such as New-ClusterGroupSet, Get-ClusterGroupSet, and Add-ClusterGroupSetDependency.  
  
## <a name="BKMK_QoS"></a>Storage quality of service \(QoS\)  
You can now create storage QoS policies on a Scale\-Out File Server and assign them to one or more virtual disks on Hyper\-V virtual machines. Storage performance is automatically readjusted to meet policies as the storage load fluctuates. For details, see [Storage Quality of Service](Storage%20Quality%20of%20Service.md).  
  
## <a name="BKMK_Config"></a>Virtual machine configuration file format  
Virtual machine configuration files use a new format that makes reading and writing configuration data more efficient. The format also makes data corruption less likely if a storage failure occurs. Virtual machine configuration data files use a .vmcx file name extension and runtime state data files use a .vmrs file name extension.  
  
> [!IMPORTANT]  
> The .vmcx file name extension indicates a binary file. Editing .vmcx or .vmrs files isn't supported.  
  
## <a name="BKMK_ConfgVersion"></a>Virtual machine configuration version  
The version represents the compatibility of the virtual machine’s configuration, saved state, and snapshot files with the version of Hyper\-V. Virtual machines with version 5 are compatible with [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)] and can run on both [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)] and [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)]. Virtual machines with versions introduced in [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] won't run in Hyper\-V on [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)].   
  
If you move or import a virtual machine to a server that runs Hyper\-V on [!INCLUDE[winthreshold_server_2](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] from [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)], the virtual machine’s configuration isn't automatically updated. This means you can move the virtual machine back to a server that runs [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)]. But, this also means you can't use the new virtual machine features until you manually update the version of the virtual machine configuration.  
  
For instructions on checking and upgrading the version, see [Upgrade virtual machine version](Upgrade%20virtual%20machine%20version%20in%20Hyper-V%20on%20Windows%2010%20or%20Windows%20Server%202016.md). This article also lists the version in which some features were introduced.   
  
> [!IMPORTANT]  
> -   After you update the  version, you can't move the virtual machine to a server that runs [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)].  
> -   You can't downgrade the configuration to a previous version.  
> -   The Update\-VMVersion cmdlet  is blocked on a Hyper\-V Cluster when the cluster functional level is [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)].  
  
## <a name="BKMK_Containers"></a>Windows Containers  
Windows Containers allow many isolated applications to run on one computer system. They're fast to build and are highly scalable and portable. Two types of container runtime are available, each with a different degree of application isolation. Windows Server Containers use namespace and process isolation. Hyper\-V Containers use a light-weight virtual machine for each container.  
  
Key features include:  
  
-	Support for web sites and applications using HTTPS  
  
-   Nano server can host both Windows Server and Hyper\-V Containers  
  
-   Ability to manage data through container shared folders  
  
-   Ability to restrict container resources  
  
For details, including quick start guides, see the [Windows Container documentation](https://msdn.microsoft.com/virtualization/windowscontainers/containers_welcome).  
  
## <a name="BKMK_PowerShellDirect"></a>Windows PowerShell Direct  
This gives you a way to run Windows PowerShell commands in a virtual machine from the host. Windows PowerShell Direct runs between the host and the virtual machine. This  means it doesn't require networking or firewall requirements, and it works regardless of your remote management configuration.  
  
Windows PowerShell Direct is an alternative to the existing tools that Hyper\-V administrators use to connect to a virtual machine on a Hyper\-V host:  
  
-   Remote management tools such as PowerShell or Remote Desktop  
  
-   Hyper\-V Virtual Machine Connection \(VMConnect\)  
  
Those tools work well, but have trade\-offs: VMConnect is reliable, but can be hard to automate. Remote PowerShell is powerful, but can be hard to set up and maintain. These trade\-offs may become more important as your Hyper\-V deployment grows. Windows PowerShell Direct addresses this by providing a powerful scripting and automation experience that's as simple as using VMConnect.   
  
For requirements and instructions, see [Manage Windows virtual machines with PowerShell Direct](https://technet.microsoft.com/library/mt187808.aspx).  
  
## See also  
[What's new in Hyper-V on Windows 10](https://msdn.microsoft.com/virtualization/hyperv_on_windows/about/whats_new)  
  
  
