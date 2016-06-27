---
title: Should I create a generation 1 or 2 virtual machine in Hyper-V?
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - techgroup-compute
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 02e31413-6140-4723-a8d6-46c7f667792d
---
# Should I create a generation 1 or 2 virtual machine in Hyper-V?
**This content is preliminary and subject to change.**  
  
Your choice to create a generation 1 or generation 2 virtual machine depends on which guest operating system you want to install and the boot method you want to use to deploy the virtual machine. We recommend that you create a generation 2 virtual machine to take advantage of features like Secure Boot unless one of the following statements is true:  
  
-   The VHD you want to boot from is not [UEFI\-compatible](http://technet.microsoft.com/library/hh824898.aspx).  
  
-   You [plan to move your virtual machine to Azure](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-questions/).  
  
-   Generation 2 doesn’t support the operating system you want to run on the virtual machine.  
  
-   Generation 2 doesn’t support the boot method you want to use.  
 
 For  more information about what features are available with generation 2 virtual machines, see [Hyper-V feature compatibility by generation and guest](https://technet.microsoft.com/library/mt695680.aspx). 
  
You can’t change a virtual machine’s generation after you’ve created it. So review the following sections in this article to make sure the generation you pick supports the operating system, boot method, and features you want to use.  
  
-   [Which guest operating systems are supported?](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_OS)  
  
-   [How can I boot the virtual machine?](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_Boot)  
  
-   [What are the advantages of using generation 2 virtual machines?](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_Advantages) 
- [What's the difference in device support?](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_DeviceCompare)
- [More about generation 2 virtual machines](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_More)

 - [Enable kernel debugging by using a COM port on a generation 2 virtual machine](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_Debug)
  
## <a name="BKMK_OS"></a>Which guest operating systems are supported?  
Generation 1 virtual machines support most guest operating systems. Generation 2 virtual machines support most 64\-bit versions of Windows and more current versions of Linux and FreeBSD operating systems. Use the following sections to see which generation of virtual machine supports the guest operating system you want to install.  
  
-   [Windows guest operating system support](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_Windows)  
  
-   [CentOS and Red Hat Enterprise Linux guest operating system support](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_CentOS)  
  
-   [Debian guest operating system support](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_Debian)  
  
-   [FreeBSD guest operating system support](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_FreeBSD)  
  
-   [Oracle Linux guest operating system support](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_Oracle)  
  
-   [SUSE guest operating system support](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_SUSE)  
  
-   [Ubuntu guest operating system support](../../compute/hyper-v/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V-.md#BKMK_Ubuntu)  
  
### <a name="BKMK_Windows"></a>Windows guest operating system support  
The following table shows which 64-bit versions of Windows you can use as a guest operating system for generation 1 and generation 2 virtual machines.  
  
|64\-bit versions of Windows|Generation 1|Generation 2|  
|-------------------------------|----------------|----------------|  
|[!INCLUDE[winblue_server_2](../../compute/hyper-v/includes/winblue_server_2_md.md)]|✔|✔|  
|[!INCLUDE[win8_server_2](../../compute/hyper-v/includes/win8_server_2_md.md)]|✔|✔|  
|Windows Server 2008 R2|✔|✖|  
|Windows Server 2008|✔|✖|  
|[!INCLUDE[winthreshold_client_1](../../compute/hyper-v/includes/winthreshold_client_1_md.md)]|✔|✔|  
|[!INCLUDE[winblue_client_2](../../compute/hyper-v/includes/winblue_client_2_md.md)]|✔|✔|  
|[!INCLUDE[win8_client_2](../../compute/hyper-v/includes/win8_client_2_md.md)]|✔|✔|  
|Windows 7|✔|✖|  
  
The following table shows which 32-bit versions of Windows you can use as a guest operating system for generation 1 and generation 2 virtual machines. 
|32\-bit versions of Windows|Generation 1|Generation 2|  
|-------------------------------|----------------|----------------|  
|[!INCLUDE[winthreshold_client_1](../../compute/hyper-v/includes/winthreshold_client_1_md.md)]|✔|✖|  
|[!INCLUDE[winblue_client_2](../../compute/hyper-v/includes/winblue_client_2_md.md)]|✔|✖|  
|[!INCLUDE[win8_client_2](../../compute/hyper-v/includes/win8_client_2_md.md)]|✔|✖|  
|Windows 7|✔|✖|  
  
For more information, see [Generation 2 Virtual Machine Overview](../Topic/Generation%202%20Virtual%20Machine%20Overview.md).  
  
### <a name="BKMK_CentOS"></a>CentOS and Red Hat Enterprise Linux guest operating system support  
The following table shows which versions of Red Hat Enterprise Linux \(RHEL\) and CentOS you can use as a guest operating system for generation 1 and generation 2 virtual machines. 
  
|Operating system versions|Generation 1|Generation 2|  
|-----------------------------|----------------|----------------|  
|RHEL\/CentOS 7.x Series|✔|✔|  
|RHEL\/CentOS 6.x Series|✔|✖|  
|RHEL\/CentOS 5.x Series|✔|✖|  
  
For more information, see [CentOS and Red Hat Enterprise Linux virtual machines on Hyper\-V](../../compute/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md).  
  
### <a name="BKMK_Debian"></a>Debian guest operating system support  
The following table shows which versions of Debian you can use as a guest operating system for generation 1 and generation 2 virtual machines. 
  
|Operating system versions|Generation 1|Generation 2|  
|-----------------------------|----------------|----------------|  
|Debian 7.0\-7.10|✔|✖|  
|Devian 8.0\-8.4|✔|✔|  
  
For more information, see [Debian virtual machines on Hyper\-V](../Topic/Supported%20Debian%20virtual%20machines%20on%20Hyper-V.md).  
  
### <a name="BKMK_FreeBSD"></a>FreeBSD guest operating system support  
The following table shows which versions of FreeBSD you can use as a guest operating system for generation 1 and generation 2 virtual machines.
|Operating system versions|Generation 1|Generation 2|  
|-----------------------------|----------------|----------------|  
|FreeBSD 10 and 10.1|✔|✖|  
|FreeBSD 9.1 and 9.3|✔|✖|  
|FreeBSD 8.4|✔|✖|  
  
For more information, see [FreeBSD virtual machines on Hyper\-V](../../compute/hyper-v/Supported-FreeBSD-virtual-machines-on-Hyper-V.md).  
  
### <a name="BKMK_Oracle"></a>Oracle Linux guest operating system support  
The following table shows which versions of Red Hat Compatible Kernel Series you can use as a guest operating system for generation 1 and generation 2 virtual machines.
|Red Hat Compatible Kernel Series versions|Generation 1|Generation 2|  
|---------------------------------------------|----------------|----------------|  
|Oracle Linux 7.x Series|✔|✔|  
|Oracle Linux 6.6, 6.5, and 6.4|✔|✖|  
  
The following table shows which versions of Unbreakable Enterprise Kernel you can use as a guest operating system for generation 1 and generation 2 virtual machines.
  
|Unbreakable Enterprise Kernel \(UEK\) versions|Generation 1|Generation 2|  
|--------------------------------------------------|----------------|----------------|  
|Oracle Linux UEK R3 QU3|✔|✖|  
|Oracle Linux UEK R3 QU2|✔|✖|  
|Oracle Linux UEK R3 QU1|✔|✖|  
  
For more information, see [Oracle Linux virtual machines on Hyper\-V](../../compute/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md).  
  
### <a name="BKMK_SUSE"></a>SUSE guest operating system support  
The following table shows which versions of SUSE you can use as a guest operating system for generation 1 and generation 2 virtual machines.

|Operating system versions|Generation 1|Generation 2|  
|-----------------------------|----------------|----------------|  
|SUSE Linux Enterprise Server 12 SP1|✔|✔|  
|SUSE Linux Enterprise Server 12|✔|✔|  
|SUSE Linux Enterprise Server 11 SP4|✔|✖|  
|SUSE Linux Enterprise Server 11 SP3|✔|✖|  
|Open SUSE 12.3|✔|✖|  
  
For more information, see [SUSE virtual machines on Hyper\-V](../Topic/Supported%20SUSE%20virtual%20machines%20on%20Hyper-V.md).  
  
### <a name="BKMK_Ubuntu"></a>Ubuntu guest operating system support  
The following table shows which versions of Ubuntu you can use as a guest operating system for generation 1 and generation 2 virtual machines.  
|Operating system versions|Generation 1|Generation 2|  
|-----------------------------|----------------|----------------|  
|Ubuntu 14.04 and later versions|✔|✔|  
|Ubuntu 12.04|✔|✖|  
  
For more information, see [Ubuntu virtual machines on Hyper\-V](../Topic/Supported%20Ubuntu%20virtual%20machines%20on%20Hyper-V.md).  
  
## <a name="BKMK_Boot"></a>How can I boot the virtual machine?  
The following table shows which boot methods are supported by generation 1 and generation 2 virtual machines.  
  
|Boot method|Generation 1|Generation 2|  
|---------------|----------------|----------------|  
|PXE boot by using a standard network adapter|✖|✔|  
|PXE boot by using a legacy network adapter|✔|✖|  
|Boot from a SCSI virtual hard disk \(.VHDX\) or virtual DVD \(.ISO\)|✖|✔|  
|Boot from IDE Controller virtual hard disk \(.VHD\) or virtual DVD \(.ISO\)|✔|✖|  
|Boot from floppy \(.VFD\)|✔|✖|  
  
## <a name="BKMK_Advantages"></a>What are the advantages of using generation 2 virtual machines?  
Here are some of the advantages you get when you use a generation 2 virtual machine:  
  
-   **Secure Boot** – This is a feature that verifies the boot loader is signed by a trusted authority in the UEFI database to help prevent unauthorized firmware, operating systems, or UEFI drivers from running at boot time. Secure Boot is enabled by default for generation 2 virtual machines. If you need to run a guest operating system that’s not supported by Secure Boot, you can disable it after the virtual machine’s created.  For more information, see [Secure Boot](assetId:///fa233171-694e-484f-95fe-1dea0ab2a310).  
  
    To Secure Boot generation 2 Linux virtual machines, you need to choose the UEFI CA Secure Boot template when you create the virtual machine.  
  
-   **Larger boot volume** \- The maximum boot volume for generation 2 virtual machines is 64TB. This is the maximum disk size supported by a .VHDX. For generation 1 virtual machines, the maximum boot volume is 2TB for a .VHDX and 2040GB for a .VHD. For more information, see [Hyper\-V Virtual Hard Disk Format Overview](assetId:///248806ae-6797-46d1-b1be-24cbf1bafba4).  
  
 You may also see a slight improvement in virtual machine boot and installation times with generation 2 virtual machines.
 
 ## <a name="BKMK_DeviceCompare"></a> What's the difference in device support?  
The following table compares the devices available between generation 1 and generation 2 virtual machines.  
  
|Generation 1 Device|Generation 2 Replacement|Generation 2 Enhancements|  
|-----------------------|----------------------------|-----------------------------|  
|IDE controller|Virtual SCSI controller|Boot from .vhdx \(64 TB maximum size, and online resize capability\)|  
|IDE CD\-ROM|Virtual SCSI CD\-ROM|Support for up to 64 SCSI DVD devices per SCSI controller.|  
|Legacy BIOS|UEFI firmware|Secure Boot|  
|Legacy network adapter|Synthetic network adapter|Network boot with IPv4 and IPv6|  
|Floppy controller and DMA controller|No floppy controller support|N/A|  
|Universal asynchronous receiver\/transmitter \(UART\) for COM ports|Optional UART for debugging|Faster and more reliable|  
|i8042 keyboard controller|Software\-based input|Uses fewer resources because there is no emulation. Also reduces the attack surface from the guest operating system.|  
|PS\/2 keyboard|Software\-based keyboard|Uses fewer resources because there is no emulation. Also reduces the attack surface from the guest operating system.|  
|PS\/2 mouse|Software\-based mouse|Uses fewer resources because there is no emulation. Also reduces the attack surface from the guest operating system.|  
|S3 video|Software\-based video|Uses fewer resources because there is no emulation. Also reduces the attack surface from the guest operating system.|  
|PCI bus|No longer required|N/A|  
|Programmable interrupt controller \(PIC\)|No longer required|N/A|  
|Programmable interval timer \(PIT\)|No longer required|N/A|  
|Super I\/O device|No longer required|N/A|  
 
 ## <a name="BKMK_More"></a> More about generation 2 virtual machines
The following sections may answer some additional questions you have about generation 2 virtual machines. 
###  Attaching or adding a DVD drive

- You can't attach a physical CD or DVD drive to a generation 2 virtual machine. The virtual DVD drive in generation 2 virtual machines only supports ISO image files. To create an ISO image file of a Windows environment, you can use the Oscdimg  command line tool. For more information, see [Oscdimg Command\-Line Options](http://msdn.microsoft.com/library/hh824847.aspx).
- When you create a new virtual machine with the New\-VM Windows PowerShell cmdlet, the generation 2 virtual machine doesn't have a DVD drive. You can add a DVD drive while the virtual machine is running.

###  Using UEFI firmware
 
- Secure Boot or UEFI firmware isn't required on the physical Hyper-V host. Hyper-V provides virtual firmware to virtual machines that is  independent of what's on the Hyper-V host.  
- UEFI firmware in a generation 2 virtual machine doesn't support setup mode for Secure Boot.   
- We don't support running a UEFI shell or other UEFI applications in a generation 2 virtual machine. Using a non\-Microsoft UEFI shell or UEFI applications is technically possible if they are compiled directly from the sources. If these applications are not appropriately digitally signed, you must disable Secure Boot for the virtual machine.
 
 ### Working with VHDX files
 
 - You can resize a VHDX file that contains the boot volume for a generation 2 virtual machine while the virtual machine is running.
- We don't support or recommend that you create a VHDX file that is bootable to both generation 1 and generation 2 virtual machines.  
- The virtual machine generation is a property of the virtual machine, not a property of the virtual hard disk. So you can't tell if a VHDX file was created by a generation 1 or a generation 2 virtual machine.  
- A VHDX file created with a generation 2 virtual machine can be attached to the IDE controller or the SCSI controller of a generation 1 virtual machine. However, if this is a bootable VHDX file, the generation 1 virtual machine won't boot.
### Using IPv6 instead of IPv4
By default, generation 2 virtual machines use IPv4. You can set a virtual machine to use IPv6 instead of IPv4 by using the [Set-VMFirmware](https://technet.microsoft.com/library/dn464287.aspx) Windows PowerShell cmdlet. For example, the following command sets the preferred protocol to IPv6 for a virtual machine named TestVM:  
  
```  
Set-VMFirmware –VMName TestVM –IPProtocolPreference IPv6  
```  

 ## <a name="BKMK_Debug"></a>Enable kernel debugging by using a COM port on a generation 2 virtual machine  
By default, COM ports are not visible in generation 2 virtual machines. You can configure COM ports by using Windows PowerShell or Windows Management Instrumentation \(WMI\).  
  
To enable kernel debugging by using a COM port, follow these steps:  
  
1.  Disable Secure Boot. Kernel debugging is not compatible with Secure Boot, so Secure Boot must be disabled in the virtual machine. Use the [Set-VMFirmware](https://technet.microsoft.com/library/dn464287.aspx) Windows PowerShell cmdlet  to disable Secure Boot when the virtual machine is in an Off state. For example, the following command disables Secure Boot on virtual machine TestVM:  
  
    ```  
    Set-VMFirmware –Vmname TestVM –EnableSecureBoot Off  
    ```  
  
2.  Configure a COM port. Use the [Set-VMComPort](https://technet.microsoft.com/library/hh848616.aspx) Windows PowerShell cmdlet to add a COM port to the virtual machine. For example, the following command configures the first COM port on virtual machine, TestVM, to connect to the named pipe, TestPipe, on the local computer:  
  
    ```  
    Set-VMComPort –VMName TestVM 1 \\.\pipe\TestPipe  
    ```  
  
> [!NOTE]  
> Configured COM ports are not visible when looking at the settings of a virtual machine in the Hyper\-V Manager console.  
   
## See Also  

[Linux and FreeBSD Virtual Machines on Hyper\-V](../Topic/Supported%20Linux%20and%20FreeBSD%20virtual%20machines%20for%20Hyper-V%20on%20Windows.md) 
[Use local resources on Hyper-V virtual machine with VMConnect](https://technet.microsoft.com/library/dn282274.aspx) 
[Plan for Hyper-V scalability in Windows Server 2016](https://technet.microsoft.com/library/jj680093.aspx)
  
