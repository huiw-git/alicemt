---
title: "Configuring Asset Intelligence in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 08e0382d-de05-4a76-ba5c-7223173f7066
caps.latest.revision: 7
caps.handback.revision: 0
author: barlanmsft
---
# Configuring Asset Intelligence in System Center Configuration Manager
You must complete a number of configuration steps before you can use Asset Intelligence in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to inventory and manage software license usage throughout your enterprise.  
  
## Steps to configure Asset Intelligence  
 To collect the inventory data required for Asset Intelligence reports, the Hardware Inventory Client Agent must be enabled. For information about enabling the Hardware Inventory Client Agent, see [How to extend hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-extend-hardware-inventory-in-System-Center-Configuration-Manager.md).  
  
|Step|Details|More Information|  
|----------|-------------|----------------------|  
|**Step 1**: Enable Asset Intelligence Hardware Inventory Reporting Classes|Asset Intelligence information collection is not enabled when [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is first installed. To enable Asset Intelligence, at least one of the required hardware inventory reporting classes that Asset Intelligence reports rely on must be enabled.|For more information, see the following procedure in this topic: [Enable Asset Intelligence hardware inventory reporting classes](#BKMK_EnableAssetIntelligence).|  
|**Step 2**: Install an Asset Intelligence Synchronization Point|The Asset Intelligence synchronization point site system role is used to connect [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites to System Center Online to synchronize Asset Intelligence catalog information. The Asset Intelligence synchronization point can be installed only on a site system located at the top-level site of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy and requires Internet access to synchronize with System Center Online by using TCP port 443.<br /><br /> In addition to downloading new Asset Intelligence catalog information, the Asset Intelligence synchronization point can upload custom software title information to System Center Online for categorization. Microsoft treats all software titles uploaded to System Center Online for categorization as public information. Therefore, you should ensure that your custom software titles do not contain confidential or proprietary information. For more information about requesting software title categorization, see [Request a catalog update for uncategorized software titles](../System Center Configuration Manager/Operations-for-Asset-Intelligence-in-System-Center-Configuration-Manager.md#BKMK_RequestCatalogUpdate).|For more information, see the following procedure in this topic: [Install an Asset Intelligence Synchronization Point](#BKMK_InstallAssetIntelligenceSynchronizationPoint).|  
|**Step 3**: Enable Auditing of Success Logon Events|Four Asset Intelligence reports display information gathered from the Windows Security event logs on client computers. If the Security event log settings are not configured to log all Success logon events, these reports contain no data even if the appropriate hardware inventory reporting class is enabled. To enable the Hardware Inventory Client Agent to inventory the information required to support these reports, you must first modify the Windows Security event log settings on clients to log all Success logon events, and enable the **SMS_SystemConsoleUser** hardware inventory reporting class.|For more information, see the following procedures in this topic: [Enable auditing of success logon events](#BKMK_EnableSuccessLogonEvents).|  
|**Step 4**: Import Software License Information|The Import Software License Wizard is used to import Microsoft Volume Licensing (MVLS) information and general license statements into the Asset Intelligence catalog.<br /><br /> The MVLS license statement contains information about the license entitlements, or number of purchased licenses, for Microsoft products.<br /><br /> A general license statement contains information about the purchased licenses for any publisher.|For more information, see the following procedures in this topic: [Import software license information](#BKMK_ImportSoftwareLicenseInformation).|  
|**Step 5**: Configure Asset Intelligence Maintenance Tasks|The following maintenance tasks are associated with Asset Intelligence. By default, both maintenance tasks are enabled and are configured on a default schedule.<br /><br /> **Check Application Title with Inventory Information**: This maintenance task checks that the software title that is reported in software inventory is reconciled with the software title in the Asset Intelligence catalog.<br /><br /> **Summarize Installed Software Data**: This maintenance task provides the information that is displayed in the **Assets and Compliance** workspace, in the **Inventoried Software** node, under the **Asset Intelligence** node. When the task runs, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] gathers a count for all inventoried software titles at the primary site.|For more information, see the following procedures in this topic: [Configure Asset Intelligence maintenance tasks](#BKMK_ConfigureMaintenanceTasks).|  
  
> [!NOTE]  
>  The **Summarize Installed Software Data** maintenance task is available only on primary sites.  
  
## Supplemental procedures for configuring Asset Intelligence  
 Use the following information for the steps in the preceding table.  
  
###  <a name="BKMK_EnableAssetIntelligence"></a> Enable Asset Intelligence hardware inventory reporting classes  
 To enable Asset Intelligence in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites, you must enable one or more Asset Intelligence hardware inventory reporting classes. You can enable the classes on the **Asset Intelligence** home page, or, in the **Administration** workspace, in the **Client Settings** node, in client settings properties. Use one of the following procedures to enable the Asset Intelligence hardware inventory reporting classes.  
  
##### To enable Asset Intelligence hardware inventory reporting classes from the Asset Intelligence home page  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Asset and Compliance**.  
  
2.  In the **Asset and Compliance** workspace, click **Asset Intelligence**.  
  
3.  On the **Home** tab, in the **Asset Intelligence** group, click **Edit Inventory Classes**. The **Edit Inventory Classes** dialog box opens.  
  
4.  To enable Asset Intelligence reporting, select **Enable all Asset Intelligence reporting classes** or select **Enable only the selected Asset Intelligence reporting classes**, and select at least one reporting class from the classes displayed.  
  
    > [!NOTE]  
    >  Asset Intelligence reports that depend on the hardware inventory classes that you enable by using this procedure do not display data until clients have scanned for and returned hardware inventory.  
  
5.  Click **OK** to enable the selected Asset Intelligence hardware inventory reporting classes.  
  
##### To enable Asset Intelligence hardware inventory reporting classes from client settings properties  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, click **Client Settings**, and then select the **Default Client Agent Settings**.  
  
    > [!NOTE]  
    >  If you have created custom client settings, you can select the custom client settings instead of the default client settings.  
  
3.  On the **Home** tab, in the **Properties** group, click **Properties**. The **Client Settings Properties** dialog box opens.  
  
4.  Click **Hardware Inventory**, and then click **Set Classes**. The **Hardware Inventory Classes** dialog box opens.  
  
5.  Click **Filter by category**, and then click **Asset Intelligence Reporting Classes**. The list of classes is refreshed with only the Asset Intelligence hardware inventory reporting classes.  
  
6.  Select at least one reporting class from the list of Asset Intelligence reporting classes.  
  
    > [!NOTE]  
    >  Asset Intelligence reports that depend on the hardware inventory classes that you enable by using this procedure do not display data until clients have scanned for and returned hardware inventory.  
  
7.  Click **OK** to enable the selected Asset Intelligence hardware inventory reporting classes.  
  
###  <a name="BKMK_InstallAssetIntelligenceSynchronizationPoint"></a> Install an Asset Intelligence Synchronization Point  
 Use the following procedure to install an Asset Intelligence synchronization point site system role.  
  
##### To install an Asset Intelligence synchronization point site system role  
  
1.  In the Configuration Manager console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, and then click **Servers and Site System Roles**.  
  
3.  Add the Asset Intelligence synchronization point site system role to a new or existing site system server by using the associated step:  
  
    -   **New site system server**: On the **Home** tab, in the **Create** group, click **Create Site System Server**. The Create Site System Server Wizard opens.  
  
        > [!NOTE]  
        >  By default, when [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs a site system role, the installation files are installed on the first available NTFS-formatted hard disk drive that has the most available free hard disk space. To prevent [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] from installing on specific drives, create an empty file named No_sms_on_drive.sms and copy it to the root folder of the drive before you install the site system server.  
  
    -   **Existing site system server**: Click the server on which you want to install the Asset Intelligence synchronization point site system role. When you click a server, a list of the site system roles that are already installed on the server are displayed in the details pane.  
  
         On the **Home** tab, in the **Server** group, click **Add Site System Role**. The Add Site System Roles Wizard opens.  
  
4.  On the **General** page, specify the general settings for the site system server. When you add the Asset Intelligence synchronization point to an existing site system server, verify the values that were previously configured.  
  
5.  On the **System Role Selection** page, select **Asset Intelligence Synchronization Point** from the list of available roles, and then click **Next**.  
  
6.  On the **Asset Intelligence Synchronization Point Connection Settings** page, click **Next**.  
  
     By default, the **Use this Asset Intelligence Synchronization Point** setting is selected and cannot be configured on this page. System Center Online accepts network traffic only over TCP port 443, therefore the **SSL port number** setting cannot be configured on this page of the wizard.  
  
7.  Optionally, you can specify a path to the System Center Online authentication certificate (.pfx) file, and then click **Next**. Typically, you do not specify a path for the certificate because the connection certificate is automatically provisioned during site role installation.  
  
8.  On the **Proxy Server Settings** page, specify whether the Asset Intelligence synchronization point will use a proxy server when connecting to System Center Online to synchronize the catalog and whether to use credentials to connect to the proxy server, and then click **Next**.  
  
    > [!WARNING]  
    >  If a proxy server is required to connect to System Center Online, the connection certificate might also be deleted if the user account password expires for the account configured for proxy server authentication.  
  
9. On the **Synchronization Schedule** page, specify whether to synchronize the Asset Intelligence catalog on a schedule. When you enable the synchronization schedule, you specify a simple or custom synchronization schedule. During scheduled synchronization, the Asset Intelligence synchronization point connects to System Center Online to retrieve the latest Asset Intelligence catalog. You can manually synchronize the Asset Intelligence catalog from the Asset Intelligence node in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. For the steps to manually synchronize the Asset Intelligence catalog, see the [To manually synchronize the Asset Intelligence catalog](../System Center Configuration Manager/Operations-for-Asset-Intelligence-in-System-Center-Configuration-Manager.md#BKMK_ManuallySynchronizeCatalog) section in the [Operations for Asset Intelligence in System Center Configuration Manager](../System Center Configuration Manager/Operations-for-Asset-Intelligence-in-System-Center-Configuration-Manager.md).  
  
10. On the **Summary** page of the New Site Role Wizard, review the settings you have specified to ensure that they are correct before you continue. To make changes to any settings, click **Previous** until you return to the appropriate page, make the change, and return to the **Summary** page.  
  
###  <a name="BKMK_EnableSuccessLogonEvents"></a> Enable auditing of success logon events  
 Use the following procedure to configure computer security policy logon settings to enable auditing of Success logon events.  
  
##### To enable success logon event logging by using a local security policy  
  
1.  On a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client computer, click **Start**, point to **Administrative Tools**, and then click **Local Security Policy**.  
  
2.  In the **Local Security Policy** dialog box, under **Security Settings**, expand **Local Policies**, and then click **Audit Policy**.  
  
3.  In the results pane, double-click **Audit logon events**, ensure that the **Success** check box is selected, and then click **OK**.  
  
##### To enable success logon event logging by using an Active Directory domain security policy  
  
1.  On a domain controller computer, click **Start**, point to **Administrative Tools**, and then click **Domain Security Policy**.  
  
2.  In the **Local Security Policy** dialog box, under **Security Settings**, expand **Local Policies**, and then click **Audit Policy**.  
  
3.  In the results pane, double-click **Audit logon events**, ensure that the **Success** check box is selected, and then click **OK**.  
  
###  <a name="BKMK_ImportSoftwareLicenseInformation"></a> Import software license information  
 The following sections describe the procedures necessary to import both Microsoft and general software licensing information into the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database by using the Import Software License Wizard. When you import software license information into the site database from license statement files, the site server computer account requires **Full Control** permissions for the NTFS file system to the file share that is used to import software license information.  
  
> [!IMPORTANT]  
>  When software license information is imported into the site database, existing software license information is overwritten. Ensure that the software license information file that you use with the Import Software License Wizard contains a complete listing of all necessary software license information.  
  
##### To import software license information into the Asset Intelligence catalog  
  
1.  In the **Asset and Compliance** workspace, click **Asset Intelligence**.  
  
2.  On the **Home** tab, in the **Asset Intelligence** group, click **Import Software Licenses**. The Import Software License Wizard opens.  
  
3.  On the **Welcome** page, click **Next**.  
  
4.  On the **Import** page, specify whether you are importing a Microsoft Volume Licensing (MVLS) file (.xml or .csv) or a General License Statement file (.csv). For more information about creating a General License Statement file, see [Create a general license statement information file for import](#BKMK_CreateGeneralLicenseStatement) later in this topic.  
  
    > [!WARNING]  
    >  To download an MVLS file in .csv format that you can import to the Asset Intelligence catalog, see [Microsoft Volume Licensing Service Center](http://go.microsoft.com/fwlink/p/?LinkId=226547). To access this information, you must have a registered account on the website. You must contact your Microsoft account representative for information about how to get your MVLS file in .xml format.  
  
5.  Enter the UNC path to the license statement file or click **Browse** to select a network shared folder and file.  
  
    > [!NOTE]  
    >  The shared folder should be correctly secured to prevent unauthorized access to the licensing information file, and the computer account of the computer that the wizard is being run on must have Full Control permissions to the share that contains the license import file.  
  
6.  On the **Summary** page, review the information you have specified to ensure that it is correct before continuing. To make any changes, click **Previous** to return to the **Import** page.  
  
###  <a name="BKMK_CreateGeneralLicenseStatement"></a> Create a general license statement information file for import  
 A general license statement can also be imported into the Asset Intelligence catalog by using a manually created license import file in comma delimited (.csv) file format.  
  
> [!NOTE]  
>  While only the **Name**, **Publisher**, **Version**, and **EffectiveQuantity** fields are required to contain data, all fields must be entered on the first row of the license import file. All date fields should be displayed in the following format: Month/Day/Year, for example, 08/04/2008.  
  
 Asset Intelligence matches the products that you specify in the general license statement by using the product name and product version, but not publisher name. You must use a product name in the general license statement that is an exact match with the product name stored in the site database. Asset Intelligence takes the **EffectiveQuantity** number given in the general license statement and compares the number with the number of installed products found in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] inventory.  
  
> [!TIP]  
>  To get a complete list of the product names stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database, you can run the following query on the site database: SELECT ProductName0 FROM v_GS_INSTALLED_SOFTWARE.  
  
 You can specify exact versions for a product or specify part of the version, such as only the major version. The following examples provide the resulting version matches for a general license statement version entry for a specific product.  
  
|General license statement entry|Matching site database entries|  
|-------------------------------------|------------------------------------|  
|Name: ”MySoftware”, ProductVersion0: ”2”|ProductName0: “Mysoftware”, ProductVersion0: “2.01.1234”<br /><br /> ProductName0: “MySoftware”, ProductVersion0: “2.02.5678”<br /><br /> ProductName0: “MySoftware”, ProductVersion0: “2.05.1234”<br /><br /> ProductName0: “MySoftware”, ProductVersion0: “2.05.5678”<br /><br /> ProductName0: “MySoftware”, ProductVersion0: “2.05.3579.000”<br /><br /> ProductName0: “MySoftware”, ProductVersion0: “2.10.1234”|  
|Name: “MySoftware”, Version “2.05”|ProductName0: “MySoftware”, ProductVersion0: “2.05.1234”<br /><br /> ProductName0: “MySoftware”, ProductVersion0: “2.05.5678”<br /><br /> ProductName0: “MySoftware”, ProductVersion0: “2.05.3579.000”|  
|Name: “Mysoftware”, Version “2”<br /><br /> Name: “Mysoftware”, Version “2.05”|Error during import. The import fails when more than one entry matches the same product version.|  
  
 The following procedure describes the process that can be used to create a general license statement import file by using Microsoft Excel.  
  
##### To create a general license statement import file by using Microsoft Excel  
  
1.  Open Microsoft Excel and create a new spreadsheet.  
  
2.  On the first row of the new spreadsheet, enter all software license data field names.  
  
3.  On the second and subsequent rows of the new spreadsheet, enter software license information as required. Ensure that at least all of the required software license data fields are entered on subsequent rows for each software license to be imported. The software title name entered in the spreadsheet must be the same as the software title that is displayed in Resource Explorer for a client computer after hardware inventory has run.  
  
4.  On the **File** menu, click **Save As**, and then save the file in .csv format.  
  
5.  Copy the .csv file to the file share that is used to import software license information into the Asset Intelligence catalog.  
  
6.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, use the Import Software License Wizard to import the newly created .csv license information file.  
  
7.  Run the Asset Intelligence **License 15A – Third Party Software Reconciliation Report** to verify that the licensing information has been successfully imported into the Asset Intelligence catalog.  
  
> [!NOTE]  
>  For an example of a general software license file that you can use for testing purposes, see [Example Asset Intelligence general license import file in System Center Configuration Manager](../System Center Configuration Manager/Example-Asset-Intelligence-general-license-import-file-in-System-Center-Configuration-Manager.md).  
  
#### Sample table to describe software licenses  
 When creating a general license statement import file, the information in the following table can be used to describe software licenses to be imported into the Asset Intelligence catalog.  
  
|Column name|Data type|Required|Example|  
|-----------------|---------------|--------------|-------------|  
|Name|Up to 255 characters|Yes|Software title|  
|Publisher|Up to 255 characters|Yes|Software publisher|  
|Version|Up to 255 characters|Yes|Software title version|  
|Language|Up to 255 characters|Yes|Software title language|  
|EffectiveQuantity|Integer value|Yes|Number of licenses purchased|  
|PONumber|Up to 255 characters|No|Purchase order information|  
|ResellerName|Up to 255 characters|No|Reseller information|  
|DateOfPurchase|Date value in the following format: MM/DD/YYYY|No|Date of license purchase|  
|SupportPurchased|Bit value|No|0 or 1: Enter 0 for Yes, or 1 for No|  
|SupportExpirationDate|Date value in the following format: MM/DD/YYYY|No|End date of purchased support|  
|Comments|Up to 255 characters|No|Optional comments|  
  
###  <a name="BKMK_ConfigureMaintenanceTasks"></a> Configure Asset Intelligence maintenance tasks  
 The following maintenance tasks are available for Asset Intelligence:  
  
-   **Check Application Title with Inventory Information**: This maintenance task checks that the software title that is reported in software inventory is reconciled with the software title in the Asset Intelligence catalog. By default, this task is enabled and scheduled to run on Saturday after 12:00 A.M. and before 5:00 A.M. This maintenance task is only available at the top-level site in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy.  
  
-   **Summarize Installed Software Data**: This maintenance task provides the information that is displayed in the **Assets and Compliance** workspace, in the **Inventoried Software** node, under the **Asset Intelligence** node. When the task runs, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] gathers a count for all inventoried software titles at the primary site. By default, this task is enabled and scheduled to run every day after 12:00 A.M. and before 5:00 A.M. This maintenance task is available only on primary sites.  
  
##### To configure Asset Intelligence maintenance tasks  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, and then click **Sites**.  
  
3.  Select the site on which to configure the Asset Intelligence maintenance task.  
  
    > [!NOTE]  
    >  The **Summarize Installed Software Data** maintenance task is available only on primary sites.  
  
4.  On the **Home** tab, in the **Settings** group, click **Site Maintenance**. A list of all available site maintenance tasks appears.  
  
5.  Select the desired maintenance task, and then click **Edit** to modify the settings.  
  
6.  Enable and configure the maintenance task. To minimize interference with the site operation, we recommend that you set the time period to off-peak hours of the site. The time period is the time interval in which the task can run. It is defined by the **Start after** and **Latest start time** specified in the **Task Properties** dialog box.  
  
    > [!WARNING]  
    >  You can initiate the task right away by selecting the current day and setting the **Start after** time to a couple minutes after the present time.  
  
7.  Click **OK** to save your settings. The task now runs according to its schedule.  
  
    > [!NOTE]  
    >  If a task fails to run on the first attempt, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] attempts to rerun the task until either the task runs successfully or until the time period in which the task can run has passed.  
  
## See Also  
 [Asset Intelligence in System Center Configuration Manager](../System Center Configuration Manager/Asset-Intelligence-in-System-Center-Configuration-Manager.md)