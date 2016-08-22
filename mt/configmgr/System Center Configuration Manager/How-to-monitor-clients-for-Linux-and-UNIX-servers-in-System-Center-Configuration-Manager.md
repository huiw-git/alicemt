---
title: "How to monitor clients for Linux and UNIX servers in System Center Configuration Manager"
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
ms.assetid: d827cf91-b18f-4ee7-b538-24ba6f003ab9
caps.latest.revision: 6
---
# How to monitor clients for Linux and UNIX servers in System Center Configuration Manager
You can view information from Linux and UNIX servers in the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console using the same methods you use to view information from Windows-based clients.  
  
 The information you can view includes:  
  
-   Status details from clients, in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console dashboards  
  
-   Details about clients in the default [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports  
  
-   Inventory details in the Resource Explorer  
  
 The following sections provide information about using the resource explorer and reports to view details about your Linux and UNIX servers.  
  
##  <a name="BKMK_UseResourceExpforLnU"></a> How to use Resource Explorer to View Inventory for Linux and UNIX Servers  
 You can view hardware and installed software details on Linux and UNIX servers by using Resource Explorer.  
  
 After a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client submits hardware inventory to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, you can use Resource Explorer to view this information. The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX does not add new classes or views for inventory to the Resource Explorer. The Linux and UNIX inventory data maps to existing WMI classes. You can view the inventory details for your Linux and UNIX servers in the Windows-based classifications using Resource Explorer.  
  
 For example, you can collect the list of all natively installed programs found on your Linux and UNIX servers. Examples of natively installed programs include **.rpms** in Linux or **.pkgs** in Solaris. After inventory has been submitted by a Linux or UNIX client, you can view the list of all the natively installed Linux or UNIX programs in Resource Explorer in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
 For information about how to use Resource Explorer, see [How to use Resource Explorer to view hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-use-Resource-Explorer-to-view-hardware-inventory-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_UseReportsforLnU"></a> How to use Reports to View Information for Linux and UNIX Servers  
 Reports for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] include information from Linux and UNIX servers along with information from Windows-based computers. No additional configurations are required to integrate the Linux and UNIX data in the reports.  
  
 For example, if you run the report named Count of Operating System Versions, it displays the list of the different operating systems and the number of clients that are running each operating system. The report is based on the hardware inventory information that was sent by the different [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients that run on the different operating systems.  
  
 It is also possible to create custom reports that are specific to Linux and UNIX server data. The **Caption** property of the hardware inventory class **Operating System** is a useful attribute that you can use to identify specific Operating Systems in the report query.  
  
 For information about reports in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [How to monitor clients in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-clients-in-System-Center-Configuration-Manager.md)   
 [Monitor and manage clients in System Center Configuration Manager](../System Center Configuration Manager/Monitor-and-manage-clients-in-System-Center-Configuration-Manager.md)