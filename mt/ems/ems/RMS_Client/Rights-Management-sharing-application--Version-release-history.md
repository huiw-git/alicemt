---
title: "Rights Management sharing application: Version release history"
ms.custom: na
ms.date: 2015-09-01
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
caps.latest.revision: 9
author: karthikaraman
manager: jeffgilb
translation.priority.ht: 
  - es-es
  - fr-fr
  - it-it
  - ko-kr
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - da-dk
  - de-de
  - hu-hu
  - ja-jp
  - nb-no
  - nl-nl
  - pl-pl
  - pt-pt
  - sv-se
---
# Rights Management sharing application: Version release history
The Rights Management team regularly updates the Rights Management sharing application for fixes and new functionality. Use the following information to see what’s new or changed in a release. The most current release is listed first.

Versions before January 1, 2015 are not listed.

> [!NOTE]
> If you have feedback or a question about the RMS sharing application, send an email message to [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question).

## Version 1.0.1908.0

|||
|-|-|
|Released <br /> <br />|9/16/2015 <br /> <br />|
|Fixes <br /> <br />|<ul><li>Support for multi-factor authentication (MFA) for Azure RMS, which also removes the dependency on the Microsoft Sign-in Assistant for applications that use modern authentication.   For more information, see the [Multi-factor authentication (MFA) and Azure RMS](../../ems/AADRightsMgmt/Requirements-for-Azure-Rights-Management.md#BKMK_MFA)   section in  [Requirements for Azure Rights Management](../../ems/AADRightsMgmt/Requirements-for-Azure-Rights-Management.md). </li> </ul>|

## Version 1.0.1784.0

|||
|-|-|
|Released <br /> <br />|7/30/2015 <br /> <br />|
|Fixes <br /> <br />|<ul><li>The default refresh interval for rights policy templates is reduced from 7 days to 1 day. </li><li>Small number of regressions and minor bugs. </li> </ul>|

## Version 1.0.1770.0

|||
|-|-|
|Released <br /> <br />|4/25/2015 <br /> <br />|
|Fixes <br /> <br />|<ul><li>Now, only owner and co-owners can remove protection. Co-authors cannot. </li><li>Files that are on a network share can now be protected. </li> </ul>|
|New features <br /> <br />|<ul><li>Support for document tracking and revocation. For more information, see [Track and revoke your documents when you use the RMS sharing application](../../ems/RMS_Client/Track-and-revoke-your-documents-when-you-use-the-RMS-sharing-application.md) </li><li>Template support when you choose **Share Protected**:<ul><li>You can now select templates. </li><li>Instead of the slider, you will see a list box that includes templates and custom permissions. </li><li>You no longer see options for **Allow consumption on all devices** and **Enforce usage restrictions**. Instead, **Generic Protection** is automatically selected, depending on the file type. </li> </ul>   For more information, see [Dialog box options for the Rights Management sharing application](../../ems/RMS_Client/Dialog-box-options-for-the-Rights-Management-sharing-application.md). </li> </ul>|

## Version 1.0.1667.0

|||
|-|-|
|Released <br /> <br />|1/19/2015 <br /> <br />|
|Fixes <br /> <br />|<ul><li>Support for Chinese language fonts in the RMS sharing app PPDF viewer. </li><li>Improved error handling and messaging. </li><li>Fix to an issue with the automatic update notification when a newer version of the app is available for download. </li> </ul>|
|New features <br /> <br />|<ul><li>**Support for multiple email domains within your organization**: If you use AD RMS and users in your organization have multiple email domains, this update lets your users consume content that has been protected by users in your organization in other domains. For more information, see the [AD RMS only: Support for multiple email domains within your organization](../../ems/RMS_Client/Rights-Management-sharing-application-administrator-guide.md#BKMK_FederatedDomains) section in the [Rights Management sharing application administrator guide](../../ems/RMS_Client/Rights-Management-sharing-application-administrator-guide.md). </li> </ul>|
