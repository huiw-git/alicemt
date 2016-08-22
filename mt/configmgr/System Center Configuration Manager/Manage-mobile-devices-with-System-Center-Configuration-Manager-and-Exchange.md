---
title: "Manage mobile devices with System Center Configuration Manager and Exchange"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: aba688d9-fd5b-4c42-8cb4-f7e1b161ef50
caps.latest.revision: 8
---
# Manage mobile devices with System Center Configuration Manager and Exchange
Use the Exchange Server connector in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] when you want to manage mobile devices that connect to Exchange Server (on-premises or online) by using the Microsoft Exchange ActiveSync protocol, and you cannot enroll them by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. You can configure Exchange mobile device management features, such as remote device wipe and settings control for multiple Exchange servers, from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
 ![configmgr&#45;with&#45;exchange](../System Center Configuration Manager/medias/configmgr-with-exchange.png "configmgr-with-exchange")  
  
 When you manage mobile devices by using the Exchange Server connector, this does not install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on the mobile devices. Some management functions are therefore limited. For example, you cannot install software on these devices or use configuration items to configure these devices. For more information about the various management capabilities that you can use with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] for mobile devices, see [Choose a device management solution for System Center Configuration Manager](../System Center Configuration Manager/Choose-a-device-management-solution-for-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  Before you install the Exchange Server connector, confirm that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the version of Microsoft Exchange that you are using. For more information, see "Exchange Server connector" in [Supported operating systems for sites and clients for System Center Configuration Manager](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md).  
  
 When you use the Exchange Server connector, the mobile devices can be managed by the settings that you configure in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] instead of being managed by the default Exchange ActiveSync mailbox policies. Define the settings that you want to use in the following group settings: **General**, **Password**, **Email Management**, **Security**, and **Application**. For example, in the **Password** group setting, you can configure whether mobile devices require a password, the minimum password length, password complexity, and whether password recovery is allowed.  
  
 When you configure at least one setting in the group, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] manages all settings in the group for mobile devices. If you do not configure any setting in a group, Exchange continues to manage the mobile devices for those settings. Any Exchange ActiveSync mailbox policies that are configured on the Exchange Server and assigned to users will still be applied.  
  
 You can also configure the Exchange Server connector to manage the Exchange access rules and allow, block, or quarantine mobile devices. You can remotely wipe mobile devices by using the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and users can remotely wipe their mobile devices by using the Application Catalog.  
  
 A user’s mobile device appears in the Application Catalog automatically when the Exchange Server connector manages it and the Exchange Server is on-premises. When you configure the Exchange Server connector for Microsoft Exchange Online, you must manually configure user device affinity for the user’s mobile device to appear in the Application Catalog. For more information about how to manually configure user device affinity, see [Link users and devices with user device affinity in System Center Configuration Manager](../System Center Configuration Manager/Link-users-and-devices-with-user-device-affinity-in-System-Center-Configuration-Manager.md).  
  
> [!TIP]  
>  If you manage a mobile device by using the Exchange Server connector and the mobile device is transferred to another user, delete the mobile device from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console before the new owner of the mobile device configures his or her Exchange account on this transferred mobile device.  
  
## Required Security Permissions  
 You must have the following security permissions to configure the Exchange Server connector:  
  
-   To add, modify, and delete the Exchange Server connector: **Modify** permission for the **Site** object.  
  
-   To configure the mobile device settings: **ModifyConnectorPolicy** permission for the **Site** object.  
  
 The **Full Administrator** security role includes the required permissions to configure the Exchange Server connector.  
  
 You must have the following security permissions to manage mobile devices:  
  
-   To wipe a mobile device: **Delete resource** for the **Collection** object.  
  
-   To cancel a wipe command: **Modify resource** for the **Collection** object.  
  
-   To allow and block mobile devices: **Modify resource** for the **Collection** object.  
  
 The **Operations Administrator** security role includes the required permissions to manage mobile devices by using the Exchange Server connector.  
  
 For more information about how to configure security permissions, see [Configure role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Configure-role-based-administration-for-System-Center-Configuration-Manager.md).  
  
## Installing and Configuring an Exchange Server Connector  
 Use the following procedure to install and configure an Exchange Server connector to manage mobile devices. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports only one connector in an Exchange organization. After you complete these steps, you can monitor the mobile devices that are found and managed by the connector when you view the collections that display mobile devices, and by using the reports for mobile devices.  
  
> [!NOTE]  
>  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] generates names for the mobile devices that it finds by using the format *UserName*_*DeviceType*. If a user has more than one mobile device that has the same device type, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] displays the same name for these mobile devices in the console and in reports.  
  
#### To install and configure an Exchange Server connector  
  
1.  Decide which account will connect to the Exchange Client Access server to manage the mobile devices. The account can be the computer account of the site server or a Windows user account. Then, configure this account to run the following Exchange Server cmdlets:  
  
    -   **Clear-ActiveSyncDevice**  
  
    -   **Get-ActiveSyncDevice**  
  
    -   **Get-ActiveSyncDeviceAccessRule**  
  
    -   **Get-ActiveSyncDeviceStatistics**  
  
    -   **Get-ActiveSyncMailboxPolicy**  
  
    -   **Get-ActiveSyncOrganizationSettings**  
  
    -   **Get-ExchangeServer**  
  
    -   **Get-Recipient**  
  
    -   **Set-ADServerSettings**  
  
    -   **Set-ActiveSyncDeviceAccessRule**  
  
    -   **Set-ActiveSyncMailboxPolicy**  
  
    -   **Set-CASMailbox**  
  
    -   **New-ActiveSyncDeviceAccessRule**  
  
    -   **New-ActiveSyncMailboxPolicy**  
  
    -   **Remove-ActiveSyncDevice**  
  
    > [!NOTE]  
    >  The following Exchange Server management roles include these cmdlets: Recipient Management, View-Only Organization Management, and Server Management. For more information about management role groups in Microsoft Exchange Server 2010, see [Understanding Management Role Groups](http://go.microsoft.com/fwlink/p/?LinkId=212914).  
  
    > [!TIP]  
    >  If you try to install or use the Exchange Server connector without the required cmdlets, you will see an error logged with the message `Invoking cmdlet <cmdlet> failed` in the EasDisc.log file on the site server computer.  
  
2.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
3.  In the **Administration** workspace, expand **Hierarchy Configuration**, and then click **Exchange Server Connectors**.  
  
4.  On the **Home** tab, in the **Create** group, click **Add Exchange Server**.  
  
5.  Complete the Add Exchange Server wizard:  
  
    -   If you use an on-premises instance of Exchange Server and specify a Client Access Server, you can specify a single server or a Client Access Server array for each Active Directory site. If the server or the array is offline, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] tries to discover a Client Access Server to use. If that fails, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] falls back to using a mailbox server to make a connection to a Client Access Server. Retries are logged as warnings in the EasDisc.log file on the site server computer. For example, search for `Failed to open runspace for site <site_name>`.  
  
    -   For the Exchange Server Connector Account, specify the account that you configured in step 1.  
  
    -   If you also enroll mobile devices by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], enable the option **External mobile device management** to ensure that these mobile devices continue to receive email from Exchange after [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] enrolls them.  
  
    -   On the **Account** page of the wizard, you can configure the account used to send email notifications to clients that are blocked by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] conditional access. The account you specify must have a valid mailbox on the Exchange server.  
  
         For more information, see [Manage access to services in System Center Configuration Manager](../System Center Configuration Manager/Manage-access-to-services-in-System-Center-Configuration-Manager.md).  
  
6.  You can verify the installation of the Exchange Server connector by using status messages and by reviewing the log files:  
  
    -   To confirm that Site Component Manager successfully installed the Exchange Server connector, look for the status ID **1015** for the **SMS_EXCHANGE_CONNECTOR** component. If [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot successfully install the connector (for example, because the specified Client Access Server computer is offline), [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] retries the installation every 60 minutes until the installation succeeds or you remove the Exchange Server connector.  
  
    -   On the site server computer, search for the SiteComp.log file, and then in the log file, search for `Component SMS_EXCHANGE_CONNECTOR flagged for installation`. A successful installation is then logged with the following text: `STATMSG: ID=1015`.  
  
## See Also  
 [Manage computers and devices with System Center Configuration Manager](../System Center Configuration Manager/Manage-computers-and-devices-with-System-Center-Configuration-Manager.md)