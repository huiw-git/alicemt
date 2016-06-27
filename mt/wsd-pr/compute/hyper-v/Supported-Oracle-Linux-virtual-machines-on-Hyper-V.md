---
title: Supported Oracle Linux virtual machines on Hyper-V
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - techgroup-compute
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c02fdb5b-62f3-43cb-a190-ab74b3ebcf77
translation.priority.mt: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - hu-hu
  - it-it
  - ja-jp
  - ko-kr
  - nl-nl
  - pl-pl
  - pt-br
  - pt-pt
  - ru-ru
  - sv-se
  - tr-tr
  - zh-cn
  - zh-tw
---
# Supported Oracle Linux virtual machines on Hyper-V
The following feature distribution map indicates the features that are present in each version. The known issues and workarounds for each distribution are listed after the table.  
  
In this section:  
  
-   [Red Hat Compatible Kernel Series](../../compute/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md#BKMK_rhc)  
  
-   [Unbreakable Enterprise Kernel Series](../../compute/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md#BKMK_uek)  
  
-   [Notes](../../compute/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md#BKMK_notes)  
  
**Table legend**  
  
-   **Built in** – LIS are included as part of this Linux distribution. The kernel module version numbers for the built in LIS \(as shown by **lsmod**, for example\) are different from the version number on the Microsoft\-provided LIS download package. A mismatch doesn't indicate that the built in LIS is out of date.  
  
-   **√** \- Feature available  
  
-   \(*blank*\) \- Feature not available  
  
-   **UEK R\*x QU\*y** \- Unbreakable Enterprise Kernel \(UEK\) where *x* is the release number and *y* is the quarterly update.  
  
## <a name="BKMK_rhc"></a>Red Hat Compatible Kernel Series  
The 32\-bit kernel for the 6.x series is PAE enabled. There is no built\-in LIS support for Oracle Linux RHCK 6.0\-6.3. Oracle Linux 7.x kernels are 64\-bit only.  
  
|**Feature**|**Windows server version**|**6.4\-6.7 and 7.0\-7.2**|**6.4\-6.7 and 7.0\-7.1**|**RHCK 7.0\-7.2**|**RHCK 6.6, 6.7, 6.8**|**RHCK 6.5**|**RHCK6.4**|  
|-|-|-|-|-|-|-|-|  
|**Availability**||[LIS 4.1](https://www.microsoft.com/download/details.aspx?id=51612)|[LIS 4.0](http://www.microsoft.com/download/details.aspx?id=46842)|Built in|Built in|Built in|Built in|  
|**[Core](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_core)**|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|√|  
|**[Networking](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Networking)**|  
|Jumbo frames|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|√|  
|VLAN tagging and trunking|2016, 2012 R2, 2012, 2008 R2|√ \(Note 1 for 6.4\-6.7\)|√ \(Note 1 for 6.4\-6.7\)|√|√ Note 1|√ Note 1|√ Note 1|  
|Live Migration|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|√|  
|Static IP Injection|2016, 2012 R2, 2012|√|√|√|√|√|√|  
|vRSS|2016, 2012 R2|√|√||√|||  
|TCP Segmentation and Checksum Offloads|2016, 2012 R2, 2012, 2008 R2|√|√||√|||  
|**[Storage](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Storage)**|  
|VHDX resize|2016, 2012 R2|√|√|√|√|√||  
|Virtual Fibre Channel|2016, 2012 R2|√ Note 2|√ Note 2|√ Note 2|√ Note 2|√ Note 2||  
|Live virtual machine backup|2016, 2012 R2|√ Note 3, 4|√ Note 3, 4|√ Note 3, 4, 11|√ Note 3, 4, 11|√ Note 3, 4, 5, 11|√ Note 3, 4, 5, 11|  
|TRIM support|2016, 2012 R2|||||||  
|SCSI WWN|2016, 2012 R2|√||||||  
|**[Memory](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Memory)**|  
|Configuration of MMIO gap|2016, 2012 R2|√|√|√|√|√|√|  
|Dynamic Memory – Hot Add|2016, 2012 R2, 2012|√ Note 7, 8, 9, 10 \(Note 6 for 6.4\-6.7\)|√ Note 7, 8, 9, 10 \(Note 6 for 6.4\-6.7\)|√ Note 6, 7, 8, 9|√ Note 6, 7, 8, 9|√ Note 6, 7, 8, 9||  
|Dynamic Memory – Ballooning|2016, 2012 R2, 2012|√ Note 7, 9, 10 \(Note 6 for 6.4\-6.7\)|√ Note 7, 9, 10 \(Note 6 for 6.4\-6.7\)|√ Note 6, 8, 9|√ Note 6, 8, 9|√ Note 6, 8, 9|√ Note 6, 8, 9, 10|  
|Manual Memory Hot\-Add|2016|||||||  
|**[Video](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Video)**|  
|Hyper\-V\-specific  video device|2016,2012 R2, 2012, 2008 R2|√|√|√|√|√||  
|**[Miscellaneous](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Misc)**|  
|Key\-Value Pair|2016, 2012 R2, 2012, 2008 R2|√|√|√ Note 12|√ Note 12|√ Note 12|√ Note 12|  
|Non\-Maskable Interrupt|2016, 2012 R2|√|√|√|√|√|√|  
|PAE Kernel Support|2016, 2012 R2, 2012, 2008 R2|√|√|N\/A|N\/A|N\/A|N\/A|  
|File copy from host to guest|2016, 2012 R2|√|√||√|||  
|lsvmbus command|2016, 2012 R2, 2012, 2008 R2|√||||||  
|Hyper-V Sockets|2016|√||||||  
|**[Generation 2 virtual machines](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_gen2)**|  
|Boot using UEFI|2016, 2012 R2|√ Note 13|√ Note 13|√ Note 13||||  
|Secure boot|2016|||||||  
  
## <a name="BKMK_uek"></a>Unbreakable Enterprise Kernel Series  
The Oracle Linux Unbreakable Enterprise Kenel \(UEK\) is 64\-bit only and has LIS support built\-in.  
  
|**Feature**|**Windows server version**|**UEK R3 QU3**|**UEK R3 QU2**|**UEK R3 QU1**|  
|-|-|-|-|-|  
|**Availability**||Built in|Built in|Built in|  
|**[Core](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_core)**|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|**[Networking](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Networking)**|  
|Jumbo frames|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|VLAN tagging and trunking|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|Live Migration|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|Static IP Injection|2016, 2012 R2, 2012|√|√||  
|vRSS|2016, 2012 R2||||  
|TCP Segmentation and Checksum Offloads|2016, 2012 R2, 2012, 2008 R2||||  
|**[Storage](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Storage)**|  
|VHDX resize|2016, 2012 R2|√|√||  
|Virtual Fibre Channel|2016, 2012 R2|√|√||  
|Live virtual machine backup|2016, 2012 R2|√ Note 3, 4, 5, 12|√ Note 3, 4, 5, 12||  
|TRIM support|2016, 2012 R2||||  
|SCSI WWN|2016, 2012 R2||||  
|**[Memory](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Memory)**|  
|Configuration of MMIO gap|2016, 2012 R2|√|√|√|  
|Dynamic Memory – Hot Add|2016, 2012 R2, 2012||||  
|Dynamic Memory – Ballooning|2016, 2012 R2, 2012||||  
|Manual Memory Hot\-Add|2016||||  
|**[Video](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Video)**|  
|Hyper\-V\-specific  video device|2016, 2012 R2, 2012, 2008 R2|√|√||  
|**[Miscellaneous](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Misc)**|  
|Key\-Value Pair|2016, 2012 R2, 2012, 2008 R2|√ Note 12|√ Note 12|√ Note 12|  
|Non\-Maskable Interrupt|2016, 2012 R2|√|√|√|  
|PAE Kernel Support|2016, 2012 R2, 2012, 2008 R2|N\/A|N\/A|N\/A|  
|File copy from host to guest|2016, 2012 R2||||  
|lsvmbus command|2016, 2012 R2, 2012, 2008 R2||||  
|Hyper-V Sockets|2016||||  
|**[Generation 2 virtual machines](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_gen2)**|  
|Boot using UEFI|2016, 2012 R2||||  
|Secure boot|2016||||  
  
## <a name="BKMK_notes"></a>Notes  
  
1.  For this Oracle Linux release, VLAN tagging works but VLAN trunking does not.  
  
2.  While using virtual fibre channel devices, ensure that logical unit number 0 \(LUN 0\) has been populated. If LUN 0 has not been populated, a Linux virtual machine might not be able to mount fibre channel devices natively.  
  
3.  If there are open file handles during a live virtual machine backup operation, then in some corner cases, the backed\-up VHDs might have to undergo a file system consistency check \(fsck\) on restore.  
  
4.  Live backup operations can fail silently if the virtual machine has an attached iSCSI device or direct\-attached storage \(also known as a pass\-through disk\).  
  
5.  Live backup support for Oracle Linux 6.4\/6.5\/UEKR3 QU2 and QU3 is available through [Hyper-V Backup Essentials for Linux](https://github.com/LIS/backupessentials/tree/1.0).  
  
6.  Dynamic memory support is only available on 64\-bit virtual machines.  
  
7.  Hot\-Add support is not enabled by default in this distribution. To enable Hot\-Add support you need to add a udev rule under \/etc\/udev\/rules.d\/ as follows:  
  
    1.  Create a file **\/etc\/udev\/rules.d\/100\-balloon.rules**. You may use any other desired name for the file.  
  
    2.  Add the following content to the file: `SUBSYSTEM=="memory", ACTION=="add", ATTR{state}="online"`  
  
    3.  Reboot the system to enable Hot\-Add support.  
  
8.  Dynamic memory operations can fail if the guest operating system is running too low on memory. The following are some best practices:  
  
    -   Startup memory and minimal memory should be equal to or greater than the amount of memory that the distribution vendor recommends.  
  
    -   Applications that tend to consume the entire available memory on a system are limited to consuming up to 80 percent of available RAM.  
  
9. If you are using Dynamic Memory on a [!INCLUDE[winthreshold_server_2_md](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] or [!INCLUDE[winblue_server_2_md](../../compute/hyper-v/includes/winblue_server_2_md.md)] operating system, specify **Startup memory**, **Minimum memory**, and **Maximum memory** parameters in multiples of 128 megabytes \(MB\). Failure to do so can lead to hot\-add failures, and you may not see any memory increase in a guest operating system.  
  
10. Certain distributions, including those using LIS 3.5 or LIS 4.0, only provide Ballooning support and do not provide Hot\-Add support. In such a scenario, the dynamic memory feature can be used by setting the Startup memory parameter to a value which is equal to the Maximum memory parameter. This results in all the requisite memory being Hot\-Added to the virtual machine at boot time and then later depending upon the memory requirements of the host, Hyper\-V can freely allocate or deallocate memory from the guest using Ballooning. Please configure **Startup Memory** and **Minimum Memory** at or above the recommended value for the distribution.  
  
11. Oracle Linux Hyper\-V daemons are not installed by default. To use these daemons, install the hyperv\-daemons package. This package conflicts with downloaded Linux Integration Services and should not be installed on systems with downloaded LIS.  
  
12. The key\/value pair \(KVP\) infrastructure might not function correctly without a Linux software update. Contact your distribution vendor to obtain the software update in case you see problems with this feature.  
  
13. On [!INCLUDE[winblue_server_2_md](../../compute/hyper-v/includes/winblue_server_2_md.md)] Generation 2 virtual machines have secure boot enabled by default and some Linux virtual machines will not boot unless the secure boot option is disabled. You can disable secure boot in the **Firmware** section of the settings for the virtual machine in **Hyper\-V Manager** or you can disable it using Powershell:  
  
    ```  
    Set-VMFirmware –VMName "VMname" -EnableSecureBoot Off  
      
    ```  
  
See Also  
  
-   [Set-VMFirmware](http://technet.microsoft.com/library/dn464287.aspx)  
  
-   [Supported CentOS and Red Hat Enterprise Linux virtual machines on Hyper-V](../../compute/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md)  
  
-   [Supported Debian virtual machines on Hyper-V](../Topic/Supported%20Debian%20virtual%20machines%20on%20Hyper-V.md)  
  
-   [Supported SUSE virtual machines on Hyper-V](../Topic/Supported%20SUSE%20virtual%20machines%20on%20Hyper-V.md)  
  
-   [Supported Ubuntu virtual machines on Hyper-V](../Topic/Supported%20Ubuntu%20virtual%20machines%20on%20Hyper-V.md)  
  
-   [Supported FreeBSD virtual machines on Hyper-V](../../compute/hyper-v/Supported-FreeBSD-virtual-machines-on-Hyper-V.md)  
  
-   [Feature Descriptions for Linux and FreeBSD virtual machines on Hyper-V](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md)  
  
-   [Best Practices for running Linux on Hyper-V](../Topic/Best%20Practices%20for%20running%20Linux%20on%20Hyper-V.md)  
