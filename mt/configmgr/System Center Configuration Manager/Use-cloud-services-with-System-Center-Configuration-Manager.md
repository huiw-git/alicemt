---
title: "Use cloud services with System Center Configuration Manager"
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
ms.assetid: 24fca61e-9cdb-447a-ad7a-f4d2e4fd6704
caps.latest.revision: 10
caps.handback.revision: 0
---
# Use cloud services with System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] supports several cloud-based options that supplement your on-premises infrastructure and can help solve business problems like:  
  
-   Manage BYOD (by using [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] for mobile device management)  
  
-   Provide content resources to isolated clients or resources on the Intranet, outside your corporate firewall (by using cloud-based distribution points)  
  
-   Scale out infrastructure when physical hardware is not available, or logically placed to support your needs (by using Microsoft Azure virtual machines)  
  
 Although provisioning cloud resources is not something you must do before you deploy [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], it can be beneficial to understand these options before progressing too far in a hierarchy design plan. The use of cloud resources might save you money and time while solving business problems that on-premises infrastructure cannot.  
  
## Cloud-based resources you can use with Configuration Manager  
 Because each option has different requirements, investigate each in greater depth to understand the unique prerequisites, limitations, and potential for additional costs based on use.  
  
-   For information about cloud-based distribution points, see  
  
-   For more information about Windows Azure, see [Windows Azure](http://go.microsoft.com/fwlink/p/?LinkId=262965) in the MSDN Library.  
  
### Microsoft Azure virtual machines<br />(for cloud-based infrastructure)  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports using computers that run in virtual machines in Azure just as it does when run on-premises within your physical corporate network. You can use Azure virtual machines in the following scenarios:  
  
-   **Scenario 1:** You can run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in a virtual machine and use it to manage clients installed in other virtual machines.  
  
-   **Scenario 2:** You can run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in a virtual machine and use it to manage clients that are not running in Azure.  
  
-   **Scenario 3:** You can run different [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system roles in virtual machines while running other roles in your physical corporate network (with appropriate network connectivity for communications).  
  
 The same requirements for networks, operating   systems, and hardware requirements that apply to installing the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] on your physical corporate network apply to the installation of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in Microsoft Azure.  
  
 Use of Azure virtual machines requires you to have an Azure subscription and you incur charges based on the number of virtual machines you use, their configuration, and use of cloud-based resources.  
  
 Additionally, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites and clients that run in Azure virtual machines are subject to the same license requirements as on-premises installations  
  
### Microsoft Azure services (for cloud-based distribution points)  
 You can use an Azure service to host a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] distribution point, which is called a called cloud-based distribution point.  You can [Use a cloud-based distribution point with System Center Configuration Manager](../System Center Configuration Manager/Use-a-cloud-based-distribution-point-with-System-Center-Configuration-Manager.md) alongside on-premises distribution points and distribution points deployed in Azure virtual machines.  
  
 This is different than using an Azure virtual machine, on which you deploy a site system role. Cloud-based distribution points:  
  
-   Run as a service in Microsoft Azure, not on a virtual machine  
  
-   Automatically scale to meet increased content requests from clients  
  
-   Support clients on the Internet and the intranet  
  
 Using Azure to hosts distribution points requires you to have an Azure subscription and you incur charges based on the amount of data that transfers to and from the service.  
  
### Microsoft Intune <br />(for mobile device management)  
 You can integrate your [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] subscription with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to enable management of devices using the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] service. This integration:  
  
-   Is called a hybrid configuration and extends [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], (or [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] depending on your perspective) to support a large variety of devices.  
  
-   Requires the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] Connector site system role.  
  
-   Requires you to have a separate [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription with sufficient licenses for the devices you will manage with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]  
  
 Although [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] uses Microsoft Azure, it does not require you to independently configure Azure, nor are you subject to additional costs beyond that of the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription.  
  
### Additional Configuration Manager capabilities  
 Some [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] capabilities can connect to cloud-based services, like:  
  
-   Windows Server Update Services (WSUS)  
  
-   The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] service cloud to download updates for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
 These additional capabilities do not require you to have an Azure subscription, nor to configure specific connections, certificates, or services in the cloud. Instead, they are automatically managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] for you.  All you need to do is ensure applicable site systems and devices can access the Internet based URLs.  
  
##  <a name="BKMK_CloudSec"></a> Security for cloud-based services  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses certificates to provision and access your content in Microsoft Azure, and to manage the services that you use. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] encrypts the data that you store in Azure, but does not introduce additional security or data controls beyond those that Azure provides.  
  
 For more information see the details for the different cloud-based resource scenarios. You can also view the following topics for Microsoft Azure security:  
  
-   [Windows Azure: Understanding Security Account Management in Windows Azure](http://go.microsoft.com/fwlink/p/?LinkId=262968)  
  
-   [Windows Azure Security Overview](http://go.microsoft.com/fwlink/p/?LinkId=262970)  
  
-   [Get Past the Security Crossroads in Your Cloud Migration](http://go.microsoft.com/fwlink/p/?LinkId=262971)  
  
-   [Data Security in Azure Part 1 of 2](http://go.microsoft.com/fwlink/p/?LinkId=262974)  
  
## See Also  
 [Prepare your network environment for System Center Configuration Manager](../System Center Configuration Manager/Prepare-your-network-environment-for-System-Center-Configuration-Manager.md)