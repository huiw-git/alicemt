---
title: "Removed and deprecated features for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: d8c8b44c-1e8a-42b6-bab4-23c72a0a6169
caps.latest.revision: 15
caps.handback.revision: 0
---
# Removed and deprecated features for System Center Configuration Manager
This topic describes features, products, and operating systems that are removed from support with [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] or will be removed in a future update (Deprecated). This is intended to provide early warning about future changes that might affect your use of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 This information is subject to change with future releases and might not include each deprecated feature, product, or operating system.  
  
## Deprecated features, products, and operating systems  
 Microsoft products and operating systems that are listed as deprecated are either in extended support or have reached end of life. Microsoft products and operating systems that are listed as deprecated are still tested with current versions of  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] until they are beyond their Microsoft support lifecycle.  For more information, see the [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle) website.  
  
 **Deprecated features:**  
  
||||  
|-|-|-|  
|**Feature**|**Deprecation first announced**|**Support removed**|  
|Network Access Protection (NAP)  - as found in [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)]|7/10/2015|√|  
|Out of Band Management - as found in [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)]|10/16/2015|√|  
  
 **Deprecated server operating systems:**  
  
||||  
|-|-|-|  
|**Operating systems**|**Deprecation first announced**|**Support removed**|  
|Windows Server 2008|7/10/2015|Support ends with the first update released after 12/31/2016  (See note 1)|  
|Windows Server 2008 R2|7/10/2015|Support ends with the first update released after 12/31/2016  (See note 2)|  
  
-   Note 1:   After support ends, this operating system will no longer be supported for site servers or most site system roles. However, it will remain supported for the distribution point site system role (including pull-distribution point) until deprecation of this support is announced or this operating system's extended support period expires.  
  
-   Note 2:    After support ends, this operating system will no longer be supported for site servers or most site system roles. However, it will remain supported for the state migration point and distribution point site system role (including pull-distribution points, and for PXE and multi-cast) until deprecation of this support is announced or this operating system's extended support period expires.  Beginning with version 1602, you can in-place upgrade the operating system of a site server from Windows Sever 2008 R2 to Windows  Server 2012 R2.  

     For more information about in-place upgrade of a site servers operating system, see the [In-place upgrade the operating system of site servers that run Windows Server 2008 R2](../System Center Configuration Manager/What-s-changed-in-System-Center-Configuration-Manager-from-System-Center-2012-Configuration-Manager.md#bkmk_UpgradeOS) section in [What's changed in System Center Configuration Manager](../System Center Configuration Manager/What-s-changed-in-System-Center-Configuration-Manager-from-System-Center-2012-Configuration-Manager.md)
       
  
  
 **Deprecated client operating systems:**  
  
 Unless noted otherwise, each operating system that is supported as a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is supported until the Extended Support End Date of that operating system, as detailed in the [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle).  If [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] support for an operating system will end prior to the Extended Support End Date, a deprecation date and support removal date for that operating system will be listed here.  
  
||||  
|-|-|-|  
|**Operating systems**|**Deprecation first announced**|**Support removed**|  
|Windows XP|7/10/2015|√|  
|Windows XP Embedded|7/10/2015|Support ends with the first update released after 12/31/2016|  
|Windows Server 2003|7/10/2015|√|  
|Windows Server 2003 R2|7/10/2015|√|  
|Windows Vista|7/10/2015|√|  
|Mac OS X  10.6 – 10.8|7/10/2015|√|  
|Windows Mobile 6.0 – 6.5|7/10/2015|√|  
|Nokia Symbian Belle|7/10/2015|√|  
|Windows CE 5.0 – 6.0|7/10/2015|√|  
  
 **Deprecated support for SQL Server versions as a site database:**  
  
||||  
|-|-|-|  
|**SQL Server versions**|**Deprecation first announced**|**Support removed**|  
|SQL Server 2008|7/10/2015|√|  
|SQL Server 2008 R2|7/10/2015|Support ends with the first update released after 12/31/2016|  
  
## Features removed in System Center Configuration Manager  
 Beginning with the initial [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] release, the following features are removed:
  
###  <a name="bkmk_amt"></a> Out of Band Management  
 With [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], native support for AMT-based computers from within the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)] has been removed.  
  
-   AMT-based computers remain fully managed when you use the [Intel SCS Add-on for Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html)  
  
-   Use of the Add-on provides you access to the latest capabilities to manage AMT while removing limitations introduced until Configuration Manager could incorporate those changes  
  
-   Out of Band Management in System Center 2012 Configuration Manager is not affected by this change  
  
###  <a name="bkmk_nap"></a> Network Access Protection  
 [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] has removed support for  Network Access Protection. The feature has been deprecated in Windows Server 2012 R2 and is removed from Windows 10.  
  
 For network access protection alternatives, see the **Deprecated functionality** section of [Network Policy and Access Services Overview](https://technet.microsoft.com/library/hh831683.aspx).  
  
## See Also  
 [Introduction to System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-System-Center-Configuration-Manager.md)