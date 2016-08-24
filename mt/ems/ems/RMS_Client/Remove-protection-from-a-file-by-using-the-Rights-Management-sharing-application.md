---
title: "Remove protection from a file by using the Rights Management sharing application"
ms.custom: na
ms.date: 2015-09-01
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - Active Directory Rights Management Services
  - Azure Rights Management
  - Windows 10
  - Windows 7 with SP1
  - Windows 8
  - Windows 8.1
ms.assetid: da95b938-eaad-4c83-a21e-ff1d4872aae4
caps.latest.revision: 25
caps.handback.revision: 0
author: karthikaraman
manager: jeffgilb
---
# Remove protection from a file by using the Rights Management sharing application
To remove protection from a file (that is, unprotect a file) that was previously protected by using the RMS sharing application, use the **Remove Protection** option from File Explorer.

> [!IMPORTANT]
> You must be an owner of the file to remove protection.

### To remove protection from a file

1.  From File Explorer, right-click the file (for example, Sample.ptxt), select **Protect with RMS**, click **Protect in-place**, and then click **Remove Protection**:

    ![Remove protection menu option for RMS sharing application](../../ems/RMS_Client/media/ADRMS_MSRMSApp_RemoveProtection.png "ADRMS_MSRMSApp_RemoveProtection")

    You might be prompted for credentials.

The original protected file is deleted (for example, Sample.ptxt) and replaced with a file that has the same name but with the unprotected file name extension (for example, Sample.txt).

## Examples and other instructions
For examples for how you might use the Rights Management sharing application, and how-to instructions, see the following sections from the Rights Management sharing application user guide:

-   [Examples for using the RMS sharing application](../../ems/RMS_Client/Rights-Management-sharing-application-user-guide.md#BKMK_SharingExamples)

-   [What do you want to do?](../../ems/RMS_Client/Rights-Management-sharing-application-user-guide.md#BKMK_SharingInstructions)

## See Also
[Rights Management sharing application user guide](../../ems/RMS_Client/Rights-Management-sharing-application-user-guide.md)

