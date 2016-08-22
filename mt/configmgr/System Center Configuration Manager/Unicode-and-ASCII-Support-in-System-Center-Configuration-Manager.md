---
title: "Unicode and ASCII Support in System Center Configuration Manager"
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
ms.assetid: 2bdec799-905f-48bc-aed5-2d92134739e8
caps.latest.revision: 6
caps.handback.revision: 0
---
# Unicode and ASCII Support in System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] creates most objects by using Unicode characters. However, several objects support ASCII characters only or they have other limitations.  
  
 The following sections list the objects that must use characters from the ASCII character set only, or that have additional limitations.  
  
-   [Objects That Use ASCII Characters](#BKMK_ASCIIchar)  
  
-   [Additional Limitations](#BKMK_OtherCharLimitations)  
  
-   [Configuration Manager Objects that Are Not Localized](#BKMK_LangNonLocalize)  
  
##  <a name="BKMK_ASCIIchar"></a> Objects that use ASCII characters  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the ASCII character set only when you create the following objects:  
  
-   Site code  
  
-   All site system server computer names  
  
-   The following Configuration Manager accounts:  
  
    > [!NOTE]  
    >  These accounts support ASCII characters and RUS characters on a site that runs in the Russian language.  
  
    -   Client Push Installation Account  
  
    -   Health State Reference Publishing Account  
  
    -   Health State Reference Querying Account  
  
    -   Management Point Database Connect Account  
  
    -   Network Access Account  
  
    -   Package Access Account  
  
    -   Standard Sender Account  
  
    -   Site System Installation Account  
  
    -   Software Update Point Connection Account  
  
    -   Software Update Point Proxy Server Account  
  
    > [!NOTE]  
    >  The accounts that you specify for role-based administration support Unicode.  
    >   
    >  The Reporting Services Point Account supports Unicode, with the exception of RUS characters.  
  
-   FQDN for site servers and site systems  
  
-   Installation path for Configuration Manager  
  
-   SQL Server instance names  
  
-   The path for the following site system roles:  
  
    -   Application Catalog web service point  
  
    -   Application Catalog website point  
  
    -   Enrollment point  
  
    -   Enrollment proxy point  
  
    -   Reporting services point  
  
    -   State migration point  
  
-   The path for the following folders:  
  
    -   The folder that stores client state migration data  
  
    -   The folder that contains the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports  
  
    -   The folder that stores the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Backup  
  
    -   The folder that stores the installation source files for site setup.  
  
    -   The folder that stores the prerequisite downloads for use by Setup  
  
-   The path for the following objects:  
  
    -   IIS website  
  
    -   Virtual application installation path  
  
    -   Virtual application name  
  
-   The following objects for AMT and out of band management:  
  
    -   The FQDN of the AMT-based computer  
  
    -   The computer name of the AMT-based computer  
  
    -   The domain NetBIOS name  
  
    -   The wireless profile name and SSID  
  
    -   The trusted root certification authority name  
  
    -   The name of the certification authority (CA) and template names  
  
    -   The file name and path for the IDE redirection image file  
  
    -   The contents of the AMT data storage  
  
-   Boot media .ISO file names  
  
##  <a name="BKMK_OtherCharLimitations"></a> Additional limitations  
 The following are additional limitations for supported character sets and language versions:  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support changing the locale of the site server computer.  
  
-   An enterprise certification authority (CA) does not support client computer names that use double-byte character sets (DBCS). The client computer names that you can use are restricted by the PKI limitation of the IA5 character set. In addition, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support CA names or subject name values that use DBCS.  
  
##  <a name="BKMK_LangNonLocalize"></a> Configuration Manager objects that are not localized  
 The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database supports Unicode for most objects that it stores, and when possible, it displays this information in the operating system language that matches the locale of a computer. For the client interface or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to display information in the computer’s operating system language, the computer’s locale must match a client or server language that you install at a site.  
  
 However, several [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] objects do not support Unicode, and they are stored in the database by using ASCII, or they have additional language limitations. This information is always displayed by using the ASCII character set or in the language that was in use when the object was created.  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)