---
title: "How to enable CRL checking for software updates in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 7b6e680a-ab8f-4144-bce3-bc36618b256c
caps.latest.revision: 5
---
# How to enable CRL checking for software updates in System Center Configuration Manager
By default, the certificate revocation list (CRL) is not checked when verifying the signature on [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] software updates. Checking the CRL each time a certificate is used offers more security against using a certificate that has been revoked, but it introduces a connection delay and incurs additional processing on the computer performing the CRL check.  
  
 If used, CRL checking must be enabled on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles that process software updates.  
  
### To enable CRL checking  
  
-   On the computer performing the CRL check, from the product DVD, run the following from a command prompt: **\SMSSETUP\BIN\X64\\**<*language*>**\UpdDwnldCfg.exe/checkrevocation**.  
  
     For example, for English (US) you would run **\SMSSETUP\BIN\X64\00000409\UpdDwnldCfg.exe /checkrevocation**  
  
## See Also  
 [Configure software updates in System Center Configuration Manager](../System Center Configuration Manager/Configure-software-updates-in-System-Center-Configuration-Manager.md)