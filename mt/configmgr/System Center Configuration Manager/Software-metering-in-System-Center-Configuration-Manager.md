---
title: "Software metering in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 8e071ea6-aba7-47be-97d7-63dcbb61d1d9
caps.latest.revision: 9
caps.handback.revision: 0
author: barlanmsft
---
# Software metering in System Center Configuration Manager
This topic contains a reference for all of the operations you might perform when using [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] software metering. For an example scenario about how to use software metering, see [Monitor app usage with software metering in System Center Configuration Manager](../System Center Configuration Manager/Monitor-app-usage-with-software-metering-in-System-Center-Configuration-Manager.md).  
  
 This topic contains the following sections:  
  
-   [Prerequisites for software metering](#BKMK_Pre)  
  
-   [Configure software metering](#BKMK_Config)  
  
-   [Create software metering rules](#BKMK_Create)  
  
-   [Configure automatic software metering rules](#BKMK_Auto)  
  
-   [Manage software metering rules](#BKMK_Manage)  
  
-   [Monitor software metering](#BKMK_Monitor)  
  
-   [Security and privacy for software metering](#BKMK_Sec)  
  
##  <a name="BKMK_Pre"></a> Prerequisites for software metering  
 Software metering has no external dependencies, only dependencies within the product.  
  
> [!IMPORTANT]  
>  Software metering is used to monitor Windows PC desktop apps with a filename ending in **.exe**. Software metering does not monitor modern Windows apps (such as those used by Windows 8).  
  
### Configuration Manager dependencies  
  
|Dependency|More information|  
|----------------|----------------------|  
|Client settings for software metering.|To use software metering, the client setting **Enable software metering on clients** must be enabled and deployed to computers. You can deploy software metering settings to all computers in the hierarchy, or you can deploy custom settings to groups of computers. For more information, see [Configure software metering](#BKMK_Config).|  
|The reporting services point.|You must configure a reporting services point before you can view software metering reports. For more information, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).|  
  
##  <a name="BKMK_Config"></a> Configure software metering  
 This procedure configures the default client settings for software metering and applies to all computers in your hierarchy. If you want these settings to apply to only some computers, create a custom device client setting and deploy it to a collection that contains the computers on which you want to use software metering. For more information about how to create custom device settings, see [How to configure client settings in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-settings-in-System-Center-Configuration-Manager.md).  
  
#### To configure software metering  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration** > **Client Settings** > **Default Client Settings**.  
  
2.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
3.  In the **Default Settings** dialog box, click **Software Metering**.  
  
4.  In the **Device Settings** list, configure the following:  
  
    -   **Enable software metering on clients**: Select **True** to enable software metering.  
  
    -   **Schedule data collection**: Configure how often software metering data is collected from client computers. Use the default value of every **7 days** or click **Schedule** to specify a custom schedule.  
  
5.  Click **OK** to close the **Default Settings** dialog box.  
  
 Client computers are configured with these settings the next time they download client policy. To initiate policy retrieval for a single client, see [How to manage clients in System Center Configuration Manager](../System Center Configuration Manager/How-to-manage-clients-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_Create"></a> Create software metering rules  
 Use the **Create Software Metering Rule Wizard** to create a new software metering rule for your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
#### To create a software metering rule  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, click **Software Metering**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Software Metering Rule**.  
  
4.  On the **General** page of the **Create Software Metering Rule Wizard**, specify the following information:  
  
    -   **Name** - The name of the software metering rule. This should be unique and descriptive.  
  
        > [!NOTE]  
        >  Software metering rules can share the same name if the file name contained in the rules is different.  
  
    -   **File Name** - The name of the program file that you want to meter. You can click **Browse** to display the **Open** dialog box, in which you can select the program file to use.  
  
        > [!NOTE]  
        >  If you type the executable file name in the **File name** box, no checks are carried out to determine whether this file exists or whether it contains the necessary header information. When possible, click **Browse** and select the executable file to be metered.  
        >   
        >  Wildcard characters are not permitted in the file name.  
        >   
        >  This box is optional if a value for **Original file name** is specified.  
  
    -   **Original File Name** - The name of the executable file that you want to meter. This name matches information in the header of the file, not the file name itself so that it can be useful in cases where the executable file has been renamed but you want to meter it by the original name.  
  
        > [!NOTE]  
        >  Wildcard characters are not permitted in the original file name.  
        >   
        >  This box is optional if a value for **File Name** is specified.  
  
    -   **Version** - The version of the executable file you that want to meter. You can use the wildcard character (*) to represent any string of characters or the wildcard character (?) to represent any single character. If you want to meter for all versions of an executable file, use the default value (\*).  
  
    -   **Language** - The language of the executable file to meter. The default value is the current locale of the operating system you are using. If you select an executable file to be metered by clicking the **Browse** button, this box is automatically filled if language information is present in the header of the file. To meter all language versions of a file, select **Any** in the drop-down list.  
  
    -   **Description** - An optional description for the software metering rule.  
  
    -   **Apply this software metering rule to the following clients** – Select whether you want to apply the software metering rule to all clients in the hierarchy or to the clients that are assigned to the site specified in the **Site** list.  
  
5.  To continue, click **Next**.  
  
6.  Review and confirm the settings and then complete the wizard to create the software metering rule. The new software metering rule is displayed in the **Software Metering** node in the **Assets and Compliance** workspace.  
  
##  <a name="BKMK_Auto"></a> Configure automatic software metering rules  
 You can configure software metering in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to automatically generate disabled software metering rules from recent usage inventory data held in the site database. You can configure this inventory data so that only for applications that are used on a specified percentage of computers metering rules are created. You can also specify the maximum number of automatically generated software metering rules allowed on the site.  
  
> [!NOTE]  
>  By default, software metering rules that are automatically created are disabled. Before you can begin to collect usage data from these rules, you must enable them.  
  
#### To configure automatic software metering rule generation  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, click **Software Metering**, and then, in the **Home** tab, in the **Settings** group, click **Software Metering Properties**.  
  
3.  In the **Software Metering Properties** dialog box, configure the following:  
  
    -   **Data retention (in days)** - Specifies the amount of time that data generated by software metering rules are kept in the site database. The default value is **90** days.  
  
    -   Enable the option **Automatically create disabled metering rules from recent usage inventory data**.  
  
    -   **Specify the percentage of computers in the hierarchy that must use a program before a software metering rule is automatically created** - The default value is **10** percent.  
  
    -   **Specify the number of software metering rules that must be exceeded in the hierarchy before the automatic creation of rules is disabled** - The default value is **100** rules.  
  
4.  Click **OK** to close the **Software Metering Properties** dialog box.  
  
##  <a name="BKMK_Manage"></a> Manage software metering rules  
 In the **Assets and Compliance** workspace, select **Software Metering**, select the software metering rule to manage, and then select a management task.  
  
 Use the following table for more information about the management tasks that might require some information before you select them.  
  
|Management Task|Details|  
|---------------------|-------------|  
|**Enable**<br /><br /> **Disable**|Enables or disables a software metering rule. This setting is downloaded to client computers according to the **Client policy polling interval** in the **Client Policy** section of client settings (by default, every 60 minutes).<br /><br /> See [How to configure client settings in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-settings-in-System-Center-Configuration-Manager.md) .|  
  
##  <a name="BKMK_Monitor"></a> Monitor software metering  
 Software metering in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] includes a number of built-in reports which allow you to monitor information about software metering operations. These reports have the report category of **Software Metering**.  
  
 For more information about how to configure reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
 Additionally, you can create queries and collections based on the data stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database by software metering.  
  
 For more information about collections in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Collections technical reference for System Center Configuration Manager](../System Center Configuration Manager/Collections-technical-reference-for-System-Center-Configuration-Manager.md).  
  
 For more information about queries in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Queries technical reference for System Center Configuration Manager](../System Center Configuration Manager/Queries-technical-reference-for-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_Sec"></a> Security and privacy for software metering  
  
### Security Issues for Software Metering  
 An attacker could send invalid software metering information to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], which will be accepted by the management point even when the software metering client setting is disabled. This might result in a large number of metering rules that are replicated throughout the hierarchy, causing a denial of service on the network and to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site servers.  
  
 Because an attacker can create invalid software metering data, do not consider software metering information to be authoritative.  
  
 Software metering is enabled by default as a client setting.  
  
###  <a name="BKMK_Privacy_Metering"></a> Privacy Information for Software Metering  
 Software metering monitors the usage of applications on client computers. Software metering is enabled by default. You must configure which applications to meter. Metering information is stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. The information is encrypted during transfer to a management point but it is not stored in encrypted form in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database.  
  
 This information is retained in the database until it is deleted by the site maintenance tasks **Delete Aged Software Metering Data** (every five days) and **Delete Aged Software Metering Summary Data** (every 270 days). You can configure the deletion interval. Metering information is not sent to Microsoft.  
  
 Before you configure software metering, consider your privacy requirements.  
  
## See Also  
 [Application management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Application-management-technical-reference-for-System-Center-Configuration-Manager.md)