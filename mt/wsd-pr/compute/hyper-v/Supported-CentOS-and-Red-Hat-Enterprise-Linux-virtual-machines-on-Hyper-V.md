---
title: Supported CentOS and Red Hat Enterprise Linux virtual machines on Hyper-V
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - techgroup-compute
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bf8783d-dee5-4b3e-8cce-2b11b117c189
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
# Supported CentOS and Red Hat Enterprise Linux virtual machines on Hyper-V
The following feature distribution maps indicate the features that are present in built\-in and downloadable versions of Linux Integration Services. The known issues and workarounds for each distribution are listed after the tables.  
  
The built-in Red Hat Enterprise Linux Integration Services drivers for Hyper-V (available since Red Hat Enterprise Linux 6.4) are sufficient for Red Hat Enterprise Linux guests to run using the high performance synthetic devices on Hyper-V hosts.  These built-in drivers are certified by Red Hat for this use. Certified configurations can be viewed on this Red Hat web page: [Red Hat Certification Catalog](https://access.redhat.com/ecosystem/search/#/ecosystem/Red%20Hat%20Enterprise%20Linux?sort=sortTitle%20asc&vendors=Microsoft&category=Server). It isn't necessary to download and install Linux Integration Services packages from the Microsoft Download Center, and doing so may limit your Red Hat support as described in Red Hat Knowledgebase article 1067: [Red Hat Knowledgebase 1067](https://access.redhat.com/articles/1067).   
  
Because of potential conflicts between the built\-in LIS support and the downloadable LIS support when you upgrade the kernel, disable automatic updates, uninstall the LIS downloadable packages, update the kernel, reboot, and then install the latest LIS release, and reboot again.  
  
In this section:  
  
-   [RHEL/CentOS 7.x Series](../../compute/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md#BKMK_7x)  
  
-   [RHEL/CentOS 6.x Series](../../compute/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md#BKMK_6x)  
  
-   [RHEL/CentOS 5.x Series](../../compute/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md#BKMK_5x)  
  
-   [Notes](../../compute/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md#BKMK_notes)  
  
**Table legend**  
  
-   **Built in** – LIS are included as part of this Linux distribution. The kernel module version numbers for the built in LIS \(as shown by **lsmod**, for example\) are different from the version number on the Microsoft\-provided LIS download package. A mismatch does not indicate that the built in LIS is out of date.  
  
-   **√** \- Feature available  
  
-   \(*blank*\) \- Feature not available  
  
## <a name="BKMK_7x"></a>RHEL\/CentOS 7.x Series  
This series only has 64\-bit kernels.  
  
|**Feature**|**Windows Server version**|**7.0\-7.2**|**7.0\-7.1**|**7.2**|**7.1**|**7.0**|  
|-|-|-|-|-|-|-|  
|**Availability**||[LIS 4.1](http://www.microsoft.com/download/details.aspx?id=51612)|[LIS 4.0](http://www.microsoft.com/download/details.aspx?id=46842)|Built in|Built in|Built in|  
|**[Core](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_core)**|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|**[Networking](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Networking)**||  
|Jumbo frames|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|VLAN tagging and trunking|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|Live Migration|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|Static IP Injection|2016, 2012 R2, 2012|√ Note 2|√ Note 2|√ Note 2|√ Note 2|√ Note 2|  
|vRSS|2016, 2012 R2|√|√|√|√||  
|TCP Segmentation and Checksum Offloads|2016, 2012 R2, 2012, 2008 R2|√|√|√|√||  
|**[Storage](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Storage)**||  
|VHDX resize|2016, 2012 R2|√|√|√|√|√|  
|Virtual Fibre Channel|2016, 2012 R2|√ Note 3|√ Note 3|√ Note 3|√ Note 3|√ Note 3|  
|Live virtual machine backup|2016, 2012 R2|√ Note 4, 5|√ Note 4, 5|√ Note 4, 5|√ Note 4, 5|√ Note 4, 5|  
|TRIM support|2016, 2012 R2||||||  
|SCSI WWN|2016, 2012 R2|√|||||  
|**[Memory](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Memory)**||  
|Configuration of MMIO gap|2016, 2012 R2|√|√|√|√|√|  
|Dynamic Memory – Hot Add|2016, 2012 R2, 2012|√ Note 8, 9, 10|√ Note 8, 9, 10|√|√|√ Note 8, 9, 10|  
|Dynamic Memory – Ballooning|2016, 2012 R2, 2012|√ Note 8, 9, 10|√ Note 9, 10|√ Note 9, 10|√ Note 9, 10|√ Note 9, 10|  
|Manual Memory Hot Add|2016 ||||||  
|**[Video](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Video)**||  
|Hyper\-V\-specific video device|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|**[Miscellaneous](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Misc)**||  
|Key\-Value Pair|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|Non\-Maskable Interrupt|2016, 2012 R2|√|√|√|√|√|  
|PAE Kernel Support|2016, 2012 R2, 2012, 2008 R2||N\/A|N\/A|N\/A|N\/A|  
|File copy from host to guest|2016, 2012 R2|√|√|√|√||  
|lsvmbus command| 2016, 2012 R2, 2012, 2008 R2 |√|||||      
|Hyper-V Sockets|2016 |√|||||  
|**[Generation 2 virtual machines](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_gen2)**||  
|Boot using UEFI|2016, 2012 R2|√ Note 14|√ Note 14|√ Note 14|√ Note 14|√ Note 14|  
|Secure boot|2016|√|√|√|√|√|  
  
## <a name="BKMK_6x"></a>RHEL\/CentOS 6.x Series  
The 32\-bit kernel for this series is PAE enabled. There is no built\-in LIS support for RHEL\/CentOS 6.0\-6.3.  
  
  
|**Feature**|**Windows Server version**|**6.0\-6.7**|**6.0\-6.7**|**6.6, 6.7, 6.8**|**6.5**|**6.4**|  
|-|-|-|-|-|-|-|  
|**Availability**||[LIS 4.1](http://www.microsoft.com/download/details.aspx?id=51612)|[LIS 4.0](http://www.microsoft.com/download/details.aspx?id=46842)|Built in|Built in|Built in|  
|**[Core](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_core)**|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|**[Networking](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Networking)**|  
|Jumbo frames|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|VLAN tagging and trunking|2016, 2012 R2, 2012, 2008 R2|√ Note 1|√ Note 1|√ Note 1|√ Note 1|√ Note 1|  
|Live Migration|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|Static IP Injection|2016, 2012 R2, 2012|√ Note 2|√ Note 2|√ Note 2|√ Note 2|√ Note 2|  
|vRSS|2016, 2012 R2|√|√|√|||  
|TCP Segmentation and Checksum Offloads|2016, 2012 R2, 2012, 2008 R2|√|√|√|||  
|**[Storage](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Storage)**|  
|VHDX resize|2016, 2012 R2|√|√|√|√||  
|Virtual Fibre Channel|2016, 2012 R2|√ Note 3|√ Note 3|√ Note 3|√ Note 3||  
|Live virtual machine backup|2016, 2012 R2|√ Note 4, 5|√ Note 4, 5|√ Note 4, 5|√ Note 4, 5, 6|√ Note 4, 5, 6|  
|TRIM support|2016, 2012 R2||||||  
|SCSI WWN|2016, 2012 R2|√|||||  
|**[Memory](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Memory)**|  
|Configuration of MMIO gap|2016, 2012 R2|√|√|√|√|√|  
|Dynamic Memory – Hot Add|2016, 2012 R2, 2012|√ Note 7, 8, 9, 10|√ Note 7, 8, 9, 10|√ Note 7, 8, 9, 10|√ Note 7, 8, 9, 10||  
|Dynamic Memory – Ballooning|2016, 2012 R2, 2012|√ Note 7, 8, 9, 10|√ Note 7, 9, 10|√ Note 7, 9, 10|√ Note 7, 9, 10|√ Note 7, 9, 10, 11|  
|Manual Memory Hot Add|2016 ||||||  
|**[Video](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Video)**|  
|Hyper\-V\-specific video device|2016, 2012 R2, 2012, 2008 R2|√|√|√|√||  
|**[Miscellaneous](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Misc)**|  
|Key\-Value Pair|2016, 2012 R2, 2012, 2008 R2|√|√|√ Note 12|√ Note 12, 13|√ Note 12, 13|  
|Non\-Maskable Interrupt|2016, 2012 R2|√|√|√|√|√|  
|PAE Kernel Support|2016, 2012 R2, 2012, 2008 R2|√|√|√|√|√|  
|File copy from host to guest|2016, 2012 R2|√|√|√|||  
|lsvmbus command| 2016, 2012 R2, 2012, 2008 R2 |√|||||  
|Hyper-V Sockets|2016 |√|||||  
|**[Generation 2 virtual machines](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_gen2)**|  
|Boot using UEFI|2016, 2012 R2||||||  
|Secure boot|2016||||||  
  
## <a name="BKMK_5x"></a>RHEL\/CentOS 5.x Series  
This series has a supported 32\-bit PAE kernel available. There is no built\-in LIS support for RHEL\/CentOS before 5.9.  
  
|**Feature**|**Windows Server version**|5.2 -5.11|**5.5\-5.11**|**5.9 – 5.11**|  
|-|-|-|-|-|  
|**Availability**||[LIS 4.1](http://www.microsoft.com/download/details.aspx?id=51612)|[LIS 4.0](http://www.microsoft.com/download/details.aspx?id=46842)|Built in|  
|**[Core](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_core)**|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|**[Networking](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Networking)**|  
|Jumbo frames|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|VLAN tagging and trunking|2016, 2012 R2, 2012, 2008 R2|√ Note 1|√ Note 1|√ Note 1|  
|Live Migration|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|Static IP Injection|2016, 2012 R2, 2012|√ Note 2|√ Note 2|√ Note 2|  
|vRSS|2016, 2012 R2||||  
|TCP Segmentation and Checksum Offloads|2016, 2012 R2, 2012, 2008 R2|√|√||  
|**[Storage](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Storage)**|  
|VHDX resize|2016, 2012 R2|√|√||  
|Virtual Fibre Channel|2016, 2012 R2|√ Note 3|√ Note 3||  
|Live virtual machine backup|2016, 2012 R2|√ Note 4, 5, 15|√ Note 4, 5|√ Note 4, 5, 6|  
|TRIM support|2016, 2012 R2||||  
|SCSI WWN|2016, 2012 R2||||  
|**[Memory](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Memory)**|  
|Configuration of MMIO gap|2016, 2012 R2|√|√|√|  
|Dynamic Memory – Hot Add|2016, 2012 R2, 2012||||  
|Dynamic Memory – Ballooning|2016, 2012 R2, 2012|√ Note 7, 9, 10, 11|√ Note 7, 9, 10, 11||  
|Manual Memory Hot Add|2016 ||||  
|**[Video](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Video)**|  
|Hyper\-V\-specific video device|2016, 2012 R2, 2012, 2008 R2|√|√||  
|**[Miscellaneous](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_Misc)**|  
|Key\-Value Pair|2016, 2012 R2, 2012, 2008 R2|√|√||  
|Non\-Maskable Interrupt|2016, 2012 R2|√|√|√|  
|PAE Kernel Support|2016, 2012 R2, 2012, 2008 R2|√|√|√|  
|File copy from host to guest|2016, 2012 R2|√|√||  
|lsvmbus command| 2016, 2012 R2, 2012, 2008 R2 ||||      
|Hyper-V Sockets|2016 ||||  
|**[Generation 2 virtual machines](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#BKMK_gen2)**|  
|Boot using UEFI|2016, 2012 R2||||  
|Secure boot|2016||||  
  
## <a name="BKMK_notes"></a>Notes  
  
1.  For this RHEL\/CentOS release, VLAN tagging works but VLAN trunking does not.  
  
2.  Static IP injection may not work if Network Manager has been configured for a given synthetic network adapter on the virtual machine. For smooth functioning of static IP injection please make sure that either Network Manager is either turned off completely or has been turned off for a specific network adapter through its ifcfg\-ethX file.  
  
3.  On [!INCLUDE[winblue_server_2_md](../../compute/hyper-v/includes/winblue_server_2_md.md)] while using virtual fibre channel devices, make sure that logical unit number 0 \(LUN 0\) has been populated. If LUN 0 has not been populated, a Linux virtual machine might not be able to mount fibre channel devices natively.  
  
4.  If there are open file handles during a live virtual machine backup operation, then in some corner cases, the backed\-up VHDs might have to undergo a file system consistency check \(fsck\) on restore.  
  
5.  Live backup operations can fail silently if the virtual machine has an attached iSCSI device or direct\-attached storage \(also known as a pass\-through disk\).  
  
6.  Live backup support for RHEL\/CentOS 5.9 – 5.11\/6.4\/6.5 is available through [Hyper-V Backup Essentials for Linux](https://github.com/LIS/backupessentials/tree/1.0).  
  
7.  Dynamic memory support is only available on 64\-bit virtual machines.  
  
8.  Hot\-Add support is not enabled by default in this distribution. To enable Hot\-Add support you need to add a udev rule under \/etc\/udev\/rules.d\/ as follows:  
  
    1.  Create a file **\/etc\/udev\/rules.d\/100\-balloon.rules**. You may use any other desired name for the file.  
  
    2.  Add the following content to the file: `SUBSYSTEM=="memory", ACTION=="add", ATTR{state}="online"`  
  
    3.  Reboot the system to enable Hot\-Add support.  
  
9. Dynamic memory operations can fail if the guest operating system is running too low on memory. The following are some best practices:  
  
    -   Startup memory and minimal memory should be equal to or greater than the amount of memory that the distribution vendor recommends.  
  
    -   Applications that tend to consume the entire available memory on a system are limited to consuming up to 80 percent of available RAM.  
  
10. If you are using Dynamic Memory on a [!INCLUDE[winthreshold_server_2_md](../../compute/hyper-v/includes/winthreshold_server_2_md.md)] or  [!INCLUDE[winblue_server_2_md](../../compute/hyper-v/includes/winblue_server_2_md.md)] operating system, specify **Startup memory**, **Minimum memory**, and **Maximum memory** parameters in multiples of 128 megabytes \(MB\). Failure to do so can lead to hot\-add failures, and you may not see any memory increase in a guest operating system.  
  
11. Certain distributions, including those using LIS 4.0 and 4.1, only provide Ballooning support and do not provide Hot\-Add support. In such a scenario, the dynamic memory feature can be used by setting the Startup memory parameter to a value which is equal to the Maximum memory parameter. This results in all the requisite memory being Hot\-Added to the virtual machine at boot time and then later depending upon the memory requirements of the host, Hyper\-V can freely allocate or deallocate memory from the guest using Ballooning. Please configure **Startup Memory** and **Minimum Memory** at or above the recommended value for the distribution.  
  
12. To enable key\/value pair \(KVP\) infrastructure, install the hypervkvpd or hyperv\-daemons rpm package from your RHEL ISO. Alternatively the package can be installed directly from RHEL repositories.  
  
13. The key\/value pair \(KVP\) infrastructure might not function correctly without a Linux software update. Contact your distribution vendor to obtain the software update in case you see problems with this feature.  
  
14. On [!INCLUDE[winblue_server_2_md](../../compute/hyper-v/includes/winblue_server_2_md.md)] Generation 2 virtual machines have secure boot enabled by default and some Linux virtual machines will not boot unless the secure boot option is disabled. You can disable secure boot in the **Firmware** section of the settings for the virtual machine in **Hyper\-V Manager** or you can disable it using Powershell:  
  
    ```  
    Set-VMFirmware –VMName "VMname" -EnableSecureBoot Off  
      
    ```  
  
15. In Red Hat Enterprise Linux or CentOS 5.2, 5.3, and 5.4 the filesystem freeze functionality is not available, so Live Virtual Machine Backup is also not available.  
   
See Also  
  
-   [Set-VMFirmware](http://technet.microsoft.com/library/dn464287.aspx)  
  
-   [Supported Debian virtual machines on Hyper-V](../Topic/Supported%20Debian%20virtual%20machines%20on%20Hyper-V.md)  
  
-   [Supported Oracle Linux virtual machines on Hyper-V](../../compute/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md)  
  
-   [Supported SUSE virtual machines on Hyper-V](../Topic/Supported%20SUSE%20virtual%20machines%20on%20Hyper-V.md)  
  
-   [Supported Ubuntu virtual machines on Hyper-V](../Topic/Supported%20Ubuntu%20virtual%20machines%20on%20Hyper-V.md)  
  
-   [Supported FreeBSD virtual machines on Hyper-V](../../compute/hyper-v/Supported-FreeBSD-virtual-machines-on-Hyper-V.md)  
  
-   [Feature Descriptions for Linux and FreeBSD virtual machines on Hyper-V](../../compute/hyper-v/Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md)  
  
-   [Best Practices for running Linux on Hyper-V](../Topic/Best%20Practices%20for%20running%20Linux%20on%20Hyper-V.md)  
  
-   [Red Hat Hardware Certification](https://hardware.redhat.com/&quicksearch=Microsoft)  
  
