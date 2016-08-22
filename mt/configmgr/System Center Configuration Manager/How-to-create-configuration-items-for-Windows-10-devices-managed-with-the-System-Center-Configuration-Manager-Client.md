---
title: "How to create configuration items for Windows 10 devices managed with the System Center Configuration Manager Client"
ms.custom: na
ms.date: 2016-06-27
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 14226fbe-dd07-4432-910b-130790624a4e
caps.latest.revision: 17
caps.handback.revision: 0
---
# How to create configuration items for Windows 10 devices managed with the System Center Configuration Manager Client
Use the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] **Windows 10** configuration item to manage settings  for Windows 10 computers that are managed by the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
> [!IMPORTANT]  
>  In this release, if you created a **Password** setting as part of a configuration item of the type **Windows 10** (for a device managed with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client), then, if the setting does not already exist, or has not been configured on the Windows 10 device, it will incorrectly evaluate as compliant.  
>   
>  As a workaround, when you create a setting for these devices, ensure that **Remediate noncompliant settings** is selected on the settings pages of the Create Configuration Item wizard. In addition, when you deploy a configuration baseline containing a Windows 10 configuration item containing password settings, select **Remediate noncompliant rules when supported** in the Deploy Configuration Baselines dialog box. By using this workaround, the setting will be monitored, and remediated if it is found to be noncompliant. After remediation, the setting will be correctly reported as **Compliant** (unless a problem is encountered in which case it will report **Error**).  
  
### To create a Windows 10 configuration item  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Configuration Items**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Configuration Item**.  
  
4.  On the **General** page of the **Create Configuration Item Wizard**, specify a name, and optional description for the configuration item.  
  
5.  Under **Specify the type of configuration item that you want to create**, select **Windows 10**.  
  
6.  Click **Categories** if you create and assign categories to help you search and filter configuration items in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
7.  On the **Supported Platforms** page of the wizard, select the specific Windows 10 platforms that will evaluate the configuration item.  
  
8.  On the **Device Settings** page of the wizard, select the settings group that you want to configure. See [Windows 10 configuration item settings reference](#BKMK_Ref) in this topic for details, and then click **Next**.  
  
    > [!TIP]  
    >  If the setting that you want is not listed, select the **Configure additional settings that are not in the default setting groups check box**.  
  
9. On each settings page, configure the settings you require, and whether you want to remediate them when they are not compliant on devices (when this is supported).  
  
10. For each settings group, you can also configure the severity that will be reported when a configuration item is found to be noncompliant from:  
  
    -   **None** - Devices that fail this compliance rule do not report a failure severity for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Information** - Devices that fail this compliance rule report a failure severity of **Information** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Warning** - Devices that fail this compliance rule report a failure severity of **Warning** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Critical** - Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Critical with event** - Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports. This severity level is also be logged as a Windows event in the application event log.  
  
11. On the **Platform Applicability** page of the wizard, review any settings that are not compatible with the supported platforms you selected earlier. You can go back and remove these settings, or you can continue.  
  
    > [!TIP]  
    >  Unsupported settings are not assessed for compliance.  
  
12. Complete the wizard.  
  
 You can view the new configuration item in the **Configuration Items** node of the **Assets and Compliance** workspace.  
  
##  <a name="BKMK_Ref"></a> Windows 10 configuration item settings reference  
  
### Password  
  
|Setting|Details|  
|-------------|-------------|  
|**Required password settings on devices**|Require a password on supported devices.|  
|**Minimum password length (characters)**|The minimum length in characters for the password.|  
|**Password expiration in days**|The number of days before the password must be changed.|  
|**Number of passwords remembered**|Prevents re-using previous passwords.|  
|**Number of failed logon attempts before a device is wiped**|Wipes the device if the login fails this number of times.|  
|**Idle time before mobile device is locked**|Specifies how many minutes the device must be inactive before it is automatically locked.|  
|**Password complexity**|Choose whether you can specify a PIN such as ‘1234’, or whether you must supply a strong password.|  
  
###  <a name="BKMK_Device"></a> Device  
  
|Setting name|Details|  
|------------------|-------------|  
|**Bluetooth**|Allows use of the Bluetooth feature on the device.|  
  
### Cloud  
  
|Setting name|Details|  
|------------------|-------------|  
|**Settings synchronization**|Allows synchronization of settings between devices.|  
|**Credentials synchronization**|Allows synchronization of credentials between devices.|  
|**Settings synchronization over metered connections**|Allow settings to be synchronized when the Internet connection is metered.|  
  
### Roaming  
  
|Setting name|Details|  
|------------------|-------------|  
|**Data roaming**|Allow roaming between networks when accessing data.|  
  
### Encryption  
  
|Setting name|Details|  
|------------------|-------------|  
|**File encryption on device**|Requires that files on the device are encrypted.|  
  
### System security  
  
|Setting name|Details|  
|------------------|-------------|  
|**User Account Control**|Configures how Windows User Account Control works on the device.<br />For example, you can disable it, or set the level at which it notifies you.|  
|**Network firewall**|Enables or disables Windows Firewall.|  
|**SmartScreen**|Enable or disable Windows SmartScreen.|  
|**Virus protection**|Requires that antivirus software must be installed and configured.|  
|**Virus protection signatures are up to date**|Requires that the signature files for the antivirus software on the device must be up to date.|  
  
### Enterprise Data Protection

With the increase of employee-owned devices in the enterprise, there’s also an increasing risk of accidental data leaks through apps and services, like email, social media, and the public cloud, which are outside of the enterprise’s control. For example, when an employee sends the latest engineering pictures from their personal email account, copies and pastes product info into a tweet, or saves an in-progress sales report to their public cloud storage.

Enterprise data protection (EDP) helps to protect against this potential data leakage without otherwise interfering with the employee experience. EDP also helps to protect enterprise apps and data against accidental data leaks on enterprise-owned devices and personal devices that employees bring to work without requiring changes to your environment or other apps.

 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] EDP configuration items manage the list of apps protected by EDP, enterprise network locations, protection level, and encryption settings.
  
> [!NOTE]  
>  Enterprise data protection is currently being tested with a number of enterprise customers, and will become available to Windows Insiders soon. To opt-in to receive preview builds of Windows, consider joining the [Windows Insider Program](https://insider.windows.com/).

For information about how to configure enterprise data protection with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Protect your enterprise data using enterprise data protection (EDP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp).
  
## See Also  
 [Configuration items for devices managed with the System Center Configuration Manager client](../System Center Configuration Manager/Configuration-items-for-devices-managed-with-the-System-Center-Configuration-Manager-client.md)