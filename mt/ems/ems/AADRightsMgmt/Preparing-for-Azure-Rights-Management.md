---
title: "Preparing for Azure Rights Management"
ms.custom: na
ms.date: 2015-10-01
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
caps.latest.revision: 25
author: karthikaraman
manager: jeffgilb
translation.priority.ht: 
  - bg-bg
  - de-de
  - el-gr
  - es-es
  - et-ee
  - fi-fi
  - fr-fr
  - hr-hr
  - it-it
  - ja-jp
  - kk-kz
  - ko-kr
  - lt-lt
  - lv-lv
  - pt-br
  - ro-ro
  - ru-ru
  - sk-sk
  - sl-si
  - sr-latn-cs
  - th-th
  - tr-tr
  - uk-ua
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - da-dk
  - hu-hu
  - nb-no
  - nl-nl
  - pl-pl
  - pt-pt
  - sv-se
---
# Preparing for Azure Rights Management
After you have signed up for a cloud subscription and established your organization with an account for [!INCLUDE[o365_1](../../ems/AADRightsMgmt/includes/o365_1_md.md)] or Azure Active Directory, you’re ready to enable the [!INCLUDE[aad_rightsmanagement_2](../../ems/AADRightsMgmt/includes/aad_rightsmanagement_2_md.md)] service.

However, before you do so, make sure that the following are in place:

-   User accounts and groups in the cloud that you create manually or that are automatically created and synchronized from Active Directory Domain Services (AD DS). Use [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) to connect your on-premises directories with Azure Active Directory.

-   Mail-enabled groups in the cloud that you will use with Rights Management. These can be built-in groups or manually created groups that contain users who will use Rights Management.

    If you have Exchange Online, you can create and use mail-enabled groups by using the Exchange admin center. If you have AD DS and are synchronizing to Azure AD, you can create and use mail-enabled groups that are either security groups or distribution groups.

## Enable Rights Management
By default, [!INCLUDE[aad_rightsmanagement_2](../../ems/AADRightsMgmt/includes/aad_rightsmanagement_2_md.md)] is disabled when you sign up for your [!INCLUDE[o365_2](../../ems/AADRightsMgmt/includes/o365_2_md.md)] or Azure AD account. To enable [!INCLUDE[aad_rightsmanagement_2](../../ems/AADRightsMgmt/includes/aad_rightsmanagement_2_md.md)] for your organization, you must activate the service. For more information, see [Activating Azure Rights Management](../../ems/AADRightsMgmt/Activating-Azure-Rights-Management.md).

## See Also
[Configuring Azure Rights Management](../../ems/AADRightsMgmt/Configuring-Azure-Rights-Management.md)

