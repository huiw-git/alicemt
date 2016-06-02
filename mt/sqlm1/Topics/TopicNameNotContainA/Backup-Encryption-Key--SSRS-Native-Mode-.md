---
title: Backup Encryption Key (SSRS Native Mode)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
robots: noindex,nofollow
---
# Backup Encryption Key (SSRS Native Mode)
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] uses an encryption key to secure sensitive data that is stored in the report server database. Having a backup of this key is essential for ensuring continued access to encrypted connection strings and credentials. You must have a backup copy of this key if you move the report server database to another computer or if you change the user name or password of the Report Server service account. Both operations require that you restore the key from a backup copy that you previously created.  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
 To open the Backup Encryption Key dialog box, click **Encryption Keys** in the navigation pane of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager, and then click **Backup**. This dialog box also appears when you update the service account using the Service Account page in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager. For more information on the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md).  
  
## Options  
 **File Location**  
 Specify a file name and location for [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] to the symmetric key. The symmetric key is never stored in plain text. You must type a password to protect the file.  
  
 **Password**  
 Type a password that protects the file against unauthorized access. Only users who know the password will be able to restore the key that is locked inside the file. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] enforces a strong password policy. The password must be at least 8 characters and include a combination of uppercase and lowercase alphanumeric characters and at least one symbol character.  
  
 **Confirm Password**  
 Re\-type the password you entered.  
  
## See Also  
 [Reporting Services Configuration Manager Help Topics](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Manager-Help-Topics.md)   
 [Back Up and Restore Reporting Services Encryption Keys](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Reporting-Services-Encryption-Keys.md)   
 [Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../Topic/Delete%20and%20Re-create%20Encryption%20Keys%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../Topic/Initialize%20a%20Report%20Server%20\(SSRS%20Configuration%20Manager\).md)   
 [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../Topic/Store%20Encrypted%20Report%20Server%20Data%20\(SSRS%20Configuration%20Manager\).md)   
 [Encryption Keys - Reporting Services Native mode &#40;Configuration Manager&#41;](../Topic/Encryption%20Keys%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md)  
  
  