---
title: "How diagnostics and usage data is used for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
caps.latest.revision: 5
---
# How diagnostics and usage data is used for System Center Configuration Manager
Diagnostic and usage data collected for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] provides Microsoft nearly immediate feedback on how the product is working (or not working), and is used to adjust future updates. We are also able to see configuration data that helps us engineer and test the configurations that are in production. For example:  
  
-   The Windows server versions that are used by site servers  
  
-   The language packs installed  
  
-   The delta of the SQL schema against the product default  
  
 This data helps the engineering team plan future tests to ensure the best experience for the most common configurations. As updates to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] are released on a faster cadence (to better support quickly moving technologies such as Windows 10 and Microsoft Intune) this data is crucial to quickly adjust and adapt.  
  
 Equally as important is how the diagnostics and usage data is not used. Microsoft does not use this data for:  
  
-   Licensing audits, such as comparing customer usage against license agreements  
  
-   Auditing of products that are out of support  
  
-   Advertising based on available data such as feature usage or geolocation (timezone)  
  
##  <a name="bkmk_improve"></a> Examples of how diagnostics and usage data is improving the product  
 Microsoft uses available data to improve to the product. The following are a few examples of how:  
  
-   **Revised support for older server operating systems:**  
  
     The initial support offered by the current branch of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] included a limit on the support timeline for Windows Server 2008 R2. After examining the usage data from customers that had upgraded to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] current branch, we identified the need to revise and extend this timeline to support the large number of customers who still use this server operating system to host site servers and site system roles.  
  
-   **Improved prerequisite checks:**  
  
     Based on the usage data, we have improved the prerequisite checks for installing an update to remove obsolete rules, account for additional cases, and in some cases to auto-remediate some issues.  
  
## See Also  
 [Diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/Diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)   
 [Levels of diagnostic usage data collection for System Center Configuration Manager](../System Center Configuration Manager/Levels-of-diagnostic-usage-data-collection-for-System-Center-Configuration-Manager.md)   
 [How diagnostics and usage data is collected by System Center Configuration Manager](../System Center Configuration Manager/How-diagnostics-and-usage-data-is-collected-by-System-Center-Configuration-Manager.md)   
 [How to view diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/How-to-view-diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)