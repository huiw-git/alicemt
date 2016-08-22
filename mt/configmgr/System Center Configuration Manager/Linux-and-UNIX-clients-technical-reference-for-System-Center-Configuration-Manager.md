---
title: "Linux and UNIX clients technical reference for System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: e5a8c79f-5791-49c5-8055-086d742e5559
caps.latest.revision: 6
---
# Linux and UNIX clients technical reference for System Center Configuration Manager
This topic contains technical information for the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] client for Linux and UNIX.  
  
##  <a name="BKMK_ComponentsofClientforLnU"></a> Component Services of the Configuration Manager Client for Linux and UNIX  
 The following table identifies the client component services of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX.  
  
|File name|More information|  
|---------------|----------------------|  
|ccmexec.bin|This service is equivalent to the ccmexc service on a Windows-based client. It is responsible for all communications with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system roles, and also communicates with the omiserver.bin service to collect hardware inventory from the local computer.<br /><br /> For a list of supported command line arguments, run **ccmexec -h**|  
|omiserver.bin|This service is the CIM server. The CIM server provides a framework for pluggable software modules called providers. Providers interact with Linux and UNIX computer resources and collect the hardware inventory data. For example, the **process provider** for a Linux computer collects data associated with the Linux operating system processes.|  
  
## Commands for the Configuration Manager client for Linux and UNIX  
 The following tables list commands that you can use to start, stop, or restart the client services (ccmexec.bin and omiserver.bin) on each version of Linux or UNIX. When you start or stop the ccmexec service, the omiserver service also starts or stops.  
  
|Operating system|Commands|  
|----------------------|--------------|  
|Universal Agent<br /><br /> RHEL 4 and SLES 9|Start: **/etc/init d/ccmexecd start**<br /><br /> Stop: **/etc/init d/ccmexecd stop**<br /><br /> Restart: **/etc/init d/ccmexecd restart**|  
|Solaris 9|Start: **/etc/init d/ccmexecd start**<br /><br /> Stop: **/etc/init d/ccmexecd stop**<br /><br /> Restart: **/etc/init d/ccmexecd restart**|  
|Solaris 10|Start:<br /><br /> **svcadm enable –s svc:/application/management/omiserver**<br /><br /> **svcadm enable –s svc:/application/management/ccmexecd**<br /><br /> Stop:<br /><br /> **svcadm disable –s svc:/application/management/ccmexecd**<br /><br /> **svcadm disable –s svc:/application/management/omiserver**|  
|Solaris 11|Start:<br /><br /> **svcadm enable –s svc:/application/management/omiserver**<br /><br /> **svcadm enable –s svc:/application/management/ccmexecd**<br /><br /> Stop:<br /><br /> **svcadm disable –s svc:/application/management/ccmexecd**<br /><br /> **svcadm disable –s svc:/application/management/omiserver**|  
|AIX|Start:<br /><br /> **startsrc –s omiserver**<br /><br /> **startsrc –s ccmexec**<br /><br /> Stop:<br /><br /> **stopsrc –s ccmexec**<br /><br /> **stopsrc –s omiserver**|  
|HP-UX|Start: **/sbin/init.d/ccmexecd start**<br /><br /> Stop: **/sbin/init.d/ccmexecd stop**<br /><br /> Restart: **/sbin/init.d/ccmexecd restart**|  
  
## See Also  
 [Client management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Client-management-technical-reference-for-System-Center-Configuration-Manager.md)