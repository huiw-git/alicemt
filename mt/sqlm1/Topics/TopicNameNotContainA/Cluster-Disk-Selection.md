---
title: Cluster Disk Selection
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
---
# Cluster Disk Selection
  Use the **Cluster Disk Selection** page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard to select the shared cluster disk resource for your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster. The cluster disk is where the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data will be placed.  
  
 A shared cluster disk is not a requirement for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] cluster installations. An SMB file server is a supported storage for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] failover cluster installations, and can be specified by using the **Database Engine – Data Directories** page before completing the installation.  
  
> [!WARNING]  
>  If you have selected Analysis Services to be installed, you must specify a shared cluster disk.  
>   
>  If you plan to enable FILESTREAM on this [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance, you must specify a shared cluster disk.  
  
## Options  
 **Shared Disks**  
 Select a single disk from the list. The cluster disk is where the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data will be placed.  
  
 Only one disk can be specified. If you select the group containing the cluster quorum resource, a warning will be displayed. We recommend that you do not install to the cluster quorum resource.  
  
 **Available Shared Disks**  
 Displays a list of available disks, whether each is qualified as a shared disk, and a description of each disk resource.  
  
  