---
title: System requirements for Hyper-V on Windows Server 2016 Technical Preview
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - techgroup-compute
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc4a4971-f727-40cd-91f5-2ee6d24b54cb
---
# System requirements for Hyper-V on Windows Server 2016 Technical Preview
**This is preliminary content and subject to change.**  
  
Hyper\-V has specific hardware requirements, and some Hyper\-V features have additional requirements. Use the details in this article to decide what requirements your system must meet so you can use Hyper\-V the way you plan to. Then, review the [Windows Server catalog](https://www.windowsservercatalog.com/). Keep in mind that requirements for Hyper\-V exceed the general minimum requirements for [!INCLUDE[winthreshold_server_2_md](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] because a virtualization environment requires more computing resources.  
  
If you're already using Hyper\-V, it's likely that you can use your existing hardware. The general hardware requirements haven't changed significantly from [!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)].  But, you will need newer hardware to use shielded virtual machines or discrete device assignment. Those features rely on specific hardware support, as described below. Other than that, the main difference in hardware is that second\-level address translation \(SLAT\) is now required instead of recommended.  
  
For details about maximum supported configurations for Hyper-V, such as the number of running virtual machines, see [Plan for Hyper-V scalability in Windows Server 2016](Plan%20for%20Hyper-V%20scalability%20in%20Windows%20Server%202016.md). The list of operating systems you can run in your virtual machines is covered in [Supported Windows guest operating systems for Hyper-V on Windows Server Technical Preview](../Topic/Supported%20Windows%20guest%20operating%20systems%20for%20Hyper-V%20on%20Windows%20Server%20Technical%20Preview.md).  

 If you're new to Hyper-V and want to learn more about it, see the [Hyper-V Technology Overview](Hyper-V%20Technology%20Overview.md).
  
## General requirements  
Regardless of the Hyper\-V features you want to use, you’ll need:  
  
-   A 64\-bit processor with second\-level address translation \(SLAT\). To install the Hyper\-V virtualization components such as Windows hypervisor, the processor must have SLAT. However, it’s not required to install Hyper\-V management tools like Virtual Machine Connection \(VMConnect\), Hyper\-V Manager, and the Hyper\-V cmdlets for Windows PowerShell. See "How to check for Hyper-V requirements," below, to find out if your processor has SLAT.  
  
-   VM Monitor Mode extensions  
  
-   Enough memory – plan for *at least* 4 GB of RAM. More memory is better. You’ll need enough memory for the host and all virtual machines that you want to run at the same time.  
  
-   Virtualization support turned on in the BIOS or UEFI:  
  
    -   Hardware\-assisted virtualization. This is available in processors that include a virtualization option — specifically processors with Intel Virtualization Technology \(Intel VT\) or AMD Virtualization \(AMD\-V\) technology.  
  
    -   Hardware\-enforced Data Execution Prevention \(DEP\) must be available and enabled. For Intel systems, this is the XD bit \(execute disable bit\). For AMD systems, this is the NX bit \(no execute bit\).  
  
## <a name="bkmk_CheckReq"></a>How to check for Hyper\-V requirements  
Open Windows PowerShell or a command prompt and type:   
```  
Systeminfo.exe  
```  
Scroll to the Hyper\-V Requirements section to review the report.  
  
## Requirements for specific features  
Here are the requirements for discrete device assignment and shielded virtual machines. For descriptions of these features, see [What's new in Hyper-V on Windows Server 2016 Technical Preview](../../compute/hyper-v/What-s-new-in-Hyper-V-on-Windows-Server-2016-Technical-Preview.md).  
  
### Discrete device assignment  
**Host** requirements are similar to the existing requirements for the SR\-IOV feature in Hyper\-V.  
  
-   The processor must have either Intel’s Extended Page Table \(EPT\) or AMD’s Nested Page Table \(NPT\).  
  
-   The chipset must have:  
  
    -   Interrupt remapping — Intel’s VT\-d with the Interrupt Remapping capability \(VT\-d2\) or any version of AMD I\/O Memory Management Unit \(I\/O MMU\).  
  
    -   DMA remapping — Intel’s VT\-d with Queued Invalidations or any AMD I\/O MMU.  
  
    -   Access control services \(ACS\) on PCI Express root ports.  
  
-   The firmware tables must expose the I\/O MMU to the Windows hypervisor. Note that this feature might be turned off in the UEFI or BIOS. For instructions, see the hardware documentation or contact your hardware manufacturer.  
  
**Devices** need GPU or non\-volatile memory express \(NVMe\). For GPU, only certain devices support discrete device assignment. To verify, see the hardware documentation or contact your hardware manufacturer. For details about this feature, including how to use it and considerations, see the post "[Discrete Device Assignment -- Description and background](http://blogs.technet.com/b/virtualization/archive/2015/11/19/discrete-device-assignment.aspx)" in the Virtualization blog.  
  
### Shielded virtual machines  
These virtual machines rely on virtualization\-based security, which supports several new features in Windows Server 2016 Technical preview.  
  
**Host** requirements are:  
-   UEFI 2.3.1c — supports secure, measured boot  
  
    The following two are optional for virtualization\-based security in general, but required for the host if you want the protection these features provide:  
  
-   TPM v2.0 — protects platform security assets  
  
-   IOMMU \(Intel VT\-D\) — so the hypervisor can provide direct memory access \(DMA\) protection  
  
**Virtual machine** requirements are:  
  
-   Generation 2  
  
-   Windows Server 2016 Technical Preview, Windows Server 2012R2 or Windows Server 2012 as the guest operating system  
  
