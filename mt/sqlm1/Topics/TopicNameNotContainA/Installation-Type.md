---
title: Installation Type
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0420c555-7a3b-42b9-8651-0b4f5bcb0008
---
# Installation Type
  Use the Installation Type page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard to specify whether to install a new instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or add features to an existing instance.  
  
## Options  
 Select the radio button that specifies your choice:  
  
-   Perform a new installation of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
  
-   Add features to an existing instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
  
     If you select the option to add features to an existing instance, use the drop\-down list to select the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to update.  
  
 You can only add the SysPrep supported features—[!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]—to a prepared image of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Other features that are not supported by SysPrep can be added after the prepared instance is completed.  
  
 **Note** You cannot add features to a failover cluster instance after it is installed. To add [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features to an existing failover cluster, you must perform a new installation to install a separate instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
  