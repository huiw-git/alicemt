---
title: "Language Packs in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: cd74e5f5-33f6-4566-8c9d-d6a93bfe71ed
caps.latest.revision: 10
---
# Language Packs in System Center Configuration Manager
This topic provides technical details about language support in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
##  <a name="BKMK_SupLanguagePacks"></a> Supported Operating System Languages  
 You can install support for the following display languages by installing **server language packs** or **client language packs** at a central administration site and at primary sites. Language pack files are downloaded when you run setup as part of the prerequisite and redistributable file download. You can also use [Setup Downloader](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md#bkmk_SetupDownloader) to download these files before you run Setup. During installation of a site, you select the server and client languages to support at that site from the available language pack files.  
  
 Use the following table to map a locale ID to a language that you want to support on servers or clients. For more information about locale IDs, see [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=252609) in the MSDN online library.  
  
### Server Languages  
  
|Server language|Locale ID (LCID)|Three letter code|  
|---------------------|------------------------|-----------------------|  
|English (default)|0409|ENU|  
|Chinese (Traditional, Hong Kong SAR)|0c04|ZHH|  
|Chinese (Simplified)|0804|CHS|  
|Chinese (Traditional, Taiwan)|0404|CHT|  
|Czech|0405|CSY|  
|Dutch - Netherlands|0413|NLD|  
|French|040c|FRA|  
|German|0407|DEU|  
|Hungarian|040e|HUN|  
|Italian - Italy|0410|ITA|  
|Japanese|0411|JPN|  
|Korean|0412|KOR|  
|Polish|0415|PLK|  
|Portuguese - Brazil|0416|PTB|  
|Portuguese - Portugal|0816|PTG|  
|Russian|0419|RUS|  
|Spanish – Spain|0c0a|ESN|  
|Swedish|041d|SVE|  
|Turkish|041f|TRK|  
  
### Client Languages  
  
|Client language|Locale ID (LCID)|Three letter code|  
|---------------------|------------------------|-----------------------|  
|English (default)|0409|ENG|  
|Chinese (Traditional, Hong Kong SAR)|0c04|ZHH|  
|Chinese -Simplified|0804|CHS|  
|Chinese (Traditional, Taiwan)|0404|CHT|  
|Czech|0405|CSY|  
|Danish|0406|DAN|  
|Dutch - Netherlands|0413|NLD|  
|Finnish|040b|FIN|  
|French|040c|FRA|  
|German|0407|DEU|  
|Greek|0408|ELL|  
|Hungarian|040e|HUN|  
|Italian - Italy|0410|ITA|  
|Japanese|0411|JPN|  
|Korean|0412|KOR|  
|Norwegian|0414|NOR|  
|Polish|0415|PLK|  
|Portuguese (Brazil)|0416|PTB|  
|Portuguese (Portugal)|0816|PTG|  
|Russian|0419|RUS|  
|Spanish - Spain|0c0a|ESN|  
|Swedish|041d|SVE|  
|Turkish|041f|TRK|  
  
### Mobile Device Client Languages  
 When you add support for mobile device languages, all mobile device client languages are included. You cannot select individual language packs for mobile device support. For information about supported languages for devices you manage with on-premises mobile device management,  see the [On-premises mobile device management](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md#bkmk_OnpremOS) section in the [Supported operating systems for sites and clients for System Center Configuration Manager](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md) topic.  
  
### How to Identify Installed Language Packs  
 You can identify the language packs that are installed on a computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client by viewing the locale ID (LCID) of the installed language packs in the computer’s registry. This information is available in the following location:  
  
-   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs**  
  
 You can use hardware inventory to collect this information, and then build a custom report to view the language details. For information about collecting custom hardware inventory, see [How to configure hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-hardware-inventory-in-System-Center-Configuration-Manager.md). For information on creating reports, see the [Manage Configuration Manager reports](../System Center Configuration Manager/Operations-and-maintenance-for-reporting-in-System-Center-Configuration-Manager.md#BKMK_ManageReports) section in the [Operations and maintenance for reporting in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-reporting-in-System-Center-Configuration-Manager.md) topic.  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)