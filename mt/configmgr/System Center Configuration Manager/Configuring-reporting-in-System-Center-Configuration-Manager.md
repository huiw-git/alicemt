---
title: "Configuring reporting in System Center Configuration Manager"
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
ms.assetid: 55ae86a7-f0ab-4c09-b4da-89cd0e7fa0e0
caps.latest.revision: 6
---
# Configuring reporting in System Center Configuration Manager
Before you can create, modify, and run reports in the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console, you must carry out a number of configuration tasks. Use the following sections in this topic to help you configure reporting in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy:  
  
-   [SQL Server Reporting Services](#BKMK_SQLReportingServices)  
  
-   [Configure reporting to Use Report Builder 3.0](#BKMK_ReportBuilder3)  
  
-   [Install a reporting services point](#BKMK_InstallReportingServicesPoint)  
  
    -   [File installation and report folder security rights](#BKMK_FileInstallationAndSecurity)  
  
-   [Reporting Services security roles for Configuration Manager](#BKMK_SecurityRoles)  
  
-   [Verify the Reporting Services Point installation](#BKMK_VerifyReportingServicesPointInstallation)  
  
-   [Configure a self-signed certificate for Configuration Manager console computers](#BKMK_Certificate)  
  
-   [Modify Reporting Services Point settings](#BKMK_ModifyReportingServicesPoint)  
  
-   [Configure report options](#BKMK_ConfigureReportOptions)  
  
 Before you proceed with installing and configuring Reporting Services in your hierarchy, review the following [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reporting topics:  
  
-   [Introduction to reporting in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-reporting-in-System-Center-Configuration-Manager.md)  
  
-   [Planning for reporting in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-reporting-in-System-Center-Configuration-Manager.md)  
  
##  <a name="BKMK_SQLReportingServices"></a> SQL Server Reporting Services  
 SQL Server Reporting Services is a server-based reporting platform that provides comprehensive reporting functionality for a variety of data sources. The reporting services point in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] communicates with SQL Server Reporting Services to copy [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports to a specified report folder, to configure Reporting Services settings, and to configure Reporting Services security settings. Reporting Services connects to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database to retrieve data that is returned when you run reports.  
  
 Before you can install the reporting services point in a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, you must install and configure SQL Server Reporting Services on the site system that hosts the reporting services point site system role. For information about installing Reporting Services, see the [SQL Server TechNet Library](http://go.microsoft.com/fwlink/p/?LinkId=266389).  
  
 Use the following procedure to verify that SQL Server Reporting Services is installed and running correctly.  
  
#### To verify that SQL Server Reporting Services is installed and running  
  
1.  On the desktop, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Reporting Services Configuration Manager**.  
  
2.  In the **Reporting Services Configuration Connection** dialog box, specify the name of the server that is hosting SQL Server Reporting Services, on the menu, select the instance of SQL Server on which you installed SQL Reporting Services, and then click **Connect**. The Reporting Services Configuration Manager opens.  
  
3.  On the **Report Server Status** page, verify that **Report Service Status** is set to **Started**. If it is not, click **Start**.  
  
4.  On the **Web Service URL** page, click the URL in **Report Service Web Service URLs** to test the connection to the report folder. The **Windows Security** dialog box might open and prompt you for security credentials. By default, your user account is displayed. Enter your password and click **OK**. Verify that the webpage opens successfully. Close the browser window.  
  
5.  On the **Database** page, verify that the **Report Server Mode** setting is configured by using **Native**.  
  
6.  On the **Report Manager URL** page, click the URL in **Report Manager Site Identification** to test the connection to the virtual directory for Report Manager. The **Windows Security** dialog box might open and prompt you for security credentials. By default, your user account is displayed. Enter your password and click **OK**. Verify that the webpage opens successfully. Close the browser window.  
  
    > [!NOTE]  
    >  Reporting Services Report Manager is not required for Reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], but it is required if you want to run reports on an Internet browser or manage reports by using Report Manager.  
  
7.  Click **Exit** to close Reporting Services [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
##  <a name="BKMK_ReportBuilder3"></a> Configure reporting to Use Report Builder 3.0  
  
#### To change the Report Builder manifest name to Report Builder 3.0  
  
1.  On the computer running the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, open the Windows Registry Editor.  
  
2.  Browse to **HKEY_LOCAL_MACHINE/SOFTWARE/Wow6432Node/Microsoft/ConfigMgr10/AdminUI/Reporting**.  
  
3.  Double-click the **ReportBuilderApplicationManifestName** key to edit the value data.  
  
4.  Change **ReportBuilder_2_0_0_0.application** to **ReportBuilder_3_0_0_0.application**, and then click **OK**.  
  
5.  Close the Windows Registry Editor.  
  
##  <a name="BKMK_InstallReportingServicesPoint"></a> Install a reporting services point  
 The reporting services point must be installed on a site to manage reports at the site. The reporting services point copies report folders and reports to SQL Server Reporting Services, applies the security policy for the reports and folders, and sets configuration settings in Reporting Services. You must configure a reporting services point before reports are displayed in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and before you can manage the reports in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. The reporting services point is a site system role that must be configured on a server with Microsoft SQL Server Reporting Services installed and running. For more information about prerequisites, see [Prerequisites for reporting in System Center Configuration Manager](../System Center Configuration Manager/Prerequisites-for-reporting-in-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  When selecting a site to install the reporting services point, keep in mind that users who will access the reports must be in the same security scope as the site where the reporting services point is installed.  
  
> [!IMPORTANT]  
>  After you install a reporting services point on a site system, do not change the URL for the report server. For example, if you create the reporting services point, and then in Reporting Services Configuration Manager you modify the URL for the report server, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console will continue to use the old URL and you will be unable to run, edit, or create reports from the console. When you must change the URL report server, remove the reporting services point, change the URL, and then reinstall the reporting services point.  
  
 Use the following procedure to install the reporting services point.  
  
#### To install the reporting services point on a site system  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, and then click **Servers and Site System Roles**.  
  
    > [!TIP]  
    >  To list only site systems that host the reporting services point site role, right-click **Servers and Site System Roles** to select **Reporting services point**.  
  
3.  Add the reporting services point site system role to a new or existing site system server by using the associated step:  
  
    > [!NOTE]  
    >  For more information about configuring site systems, see [Add site system roles for System Center Configuration Manager](../System Center Configuration Manager/Add-site-system-roles-for-System-Center-Configuration-Manager.md).  
  
    -   **New site system**: On the **Home** tab, in the **Create** group, click **Create Site System Server**. The **Create Site System Server Wizard** opens.  
  
    -   **Existing site system**: Click the server on which you want to install the reporting services point site system role. When you click a server, a list of the site system roles that are already installed on the server are displayed in the results pane.  
  
         On the **Home** tab, in the **Server** group, click **Add Site System Role**. The **Add Site System Roles Wizard** opens.  
  
4.  On the **General** page, specify the general settings for the site system server. When you add the reporting services point to an existing site system server, verify the values that you previously configured.  
  
5.  On the **System Role Selection** page, select **Reporting services point** in the list of available roles, and then click **Next**.  
  
6.  On the **Reporting services Point** page, configure the following settings:  
  
    -   **Site database server name**: Specify the name of the server that hosts the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database. Typically, the wizard automatically retrieves the fully qualified domain name (FQDN) for the server. To specify a database instance, use the format <*Server Name*>\\<*Instance Name*>.  
  
    -   **Database name**: Specify the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database name, and then click **Verify** to confirm that the wizard has access to the site database.  
  
        > [!IMPORTANT]  
        >  The user account that is creating the reporting services point must have **Read** access to the site database. If the connection test fails, a red warning icon appears. Move the cursor over this icon to read details of the failure. Correct the failure, and then click **Test** again.  
  
    -   **Folder name**: Specify the folder name that is created and used to host the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports in Reporting Services.  
  
    -   **Reporting Services server instance**: Select in the list the instance of SQL Server for Reporting Services. When there is only one instance found, by default, it is listed and selected. When no instances are found, verify that SQL Server Reporting Services is installed and configured, and that the SQL Server Reporting Services service is started on the site system.  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] makes a connection in the context of the current user to Windows Management Instrumentation (WMI) on the selected site system to retrieve the instance of SQL Server for Reporting Services. The current user must have **Read** access to WMI on the site system, or the Reporting Services instances cannot be retrieved.  
  
    -   **Reporting Services Point Account**: Click **Set**, and then select an account to use when SQL Server Reporting Services on the reporting services point connects to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database to retrieve the data that are displayed in a report. Select **Existing account** to specify a Windows user account that has previously been configured as a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] account, or select **New account** to specify a Windows user account that is not currently configured as a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] account. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically grants the specified user access to the site database. The user is displayed in the **Accounts** subfolder of the **Security** node in the **Administration** workspace with the **ConfigMgr Reporting Services Point** account name.  
  
         The account that runs Reporting Services must belong to the domain local security group **Windows Authorization Access Group**, and have the **Read tokenGroupsGlobalAndUniversal** permission set to **Allow**.  
  
         The specified Windows user account and password are encrypted and stored in the Reporting Services database. Reporting Services retrieves the data for reports from the site database by using this account and password.  
  
        > [!IMPORTANT]  
        >  The account that you specify must have **Log on Locally** permissions on the computer hosting the Reporting Services database.  
  
7.  On the **Reporting Services Point** page, click **Next**.  
  
8.  On the **Summary** page, verify the settings, and then click **Next** to install the reporting services point.  
  
     After the wizard is completed, report folders are created, and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports are copied to the specified report folders.  
  
    > [!NOTE]  
    >  When report folders are created and reports are copied to the report server, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] determines the appropriate language for the objects. If the associated language pack is installed on the site, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] creates the objects in the same language as the operating system running on the report server on the site. If the language is not available, the reports are created and displayed in English. When you install a reporting services point on a site without language packs, the reports are installed in English. If you install a language pack after you install the reporting services point, you must uninstall and reinstall the reporting services point for the reports to be available in the appropriate language pack language. For more information about language packs, see [Language Packs in System Center Configuration Manager](../System Center Configuration Manager/Language-Packs-in-System-Center-Configuration-Manager.md).  
  
###  <a name="BKMK_FileInstallationAndSecurity"></a> File installation and report folder security rights  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] performs the following actions to install the reporting services point and to configure Reporting Services:  
  
> [!IMPORTANT]  
>  The actions in the following list are performed by using the credentials of the account that is configured for the SMS_Executive service, which typically is the site server local system account.  
  
-   Installs the reporting services point site role.  
  
-   Creates the data source in Reporting Services with the stored credentials that you specified in the wizard. This is the Windows user account and password that Reporting Services uses to connect to the site database when you run reports.  
  
-   Creates the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] root folder in Reporting Services.  
  
-   Adds the **ConfigMgr Report Users** and **ConfigMgr Report Administrators** security roles in Reporting Services.  
  
-   Creates subfolders and deploys [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports from %ProgramFiles%\SMS_SRSRP to Reporting Services.  
  
-   Adds the **ConfigMgr Report Users** role in Reporting Services to the root folders for all user accounts in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] that have **Site Read** rights.  
  
-   Adds the **ConfigMgr Report Administrators** role in Reporting Services to the root folders for all user accounts in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] that have **Site Modify** rights.  
  
-   Retrieves the mapping between report folders and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] secured object types (maintained in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database).  
  
-   Configures the following rights for administrative users in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to specific report folders in Reporting Services:  
  
    -   Adds users and assigns the **ConfigMgr Report Users** role to the associated report folder for administrative users who have **Run Report** permissions for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] object.  
  
    -   Adds users and assigns the **ConfigMgr Report Administrators** role to the associated report folder for administrative users who have **Modify Report** permissions for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] object.  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] connects to Reporting Services and sets the permissions for users on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and Reporting Services root folders and specific report folders. After the initial installation of the reporting services point, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] connects to Reporting Services in a 10-minute interval to verify that the user rights configured on the report folders are the associated rights that are set for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] users. When users are added or user rights are modified on the report folder by using Reporting Services Report Manager, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] overwrites those changes by using the role-based assignments stored in the site database. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] also removes users that do not have Reporting rights in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
##  <a name="BKMK_SecurityRoles"></a> Reporting Services security roles for Configuration Manager  
 When [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs the reporting services point, adds the following security roles in Reporting Services:  
  
-   **ConfigMgr Report Users**: Users assigned with this security role can only run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
-   **ConfigMgr Report Administrators**: Users assigned with this security role can perform all tasks related to reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
##  <a name="BKMK_VerifyReportingServicesPointInstallation"></a> Verify the Reporting Services Point installation  
 After you add the reporting services point site role, you can verify the installation by looking at specific status messages and log file entries. Use the following procedure to verify that the reporting services point installation was successful.  
  
> [!WARNING]  
>  You can skip this procedure if reports are displayed in the **Reports** subfolder of the **Reporting** node in the **Monitoring** workspace in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
#### To verify the reporting services point installation  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the **Monitoring** workspace, expand **System Status**, and then click **Component Status**.  
  
3.  Click **SMS_SRS_REPORTING_POINT** in the list of components.  
  
4.  On the **Home** tab, in the **Component** group, click **Show Messages**, and then click **All**.  
  
5.  Specify a date and time for a period before you installed the reporting services point, and then click **OK**.  
  
6.  Verify that status message ID 1015 is listed, which indicates that the reporting services point was successfully installed. Alternatively, you can open the Srsrp.log file, located in <*ConfigMgr Installation Path*>\Logs, and look for **Installation was successful**.  
  
     In Windows Explorer, navigate to <*ConfigMgr Installation Path*>\Logs.  
  
7.  Open Srsrp.log and step through the log file starting from the time that the reporting services point was successfully installed. Verify that the report folders were created, the reports were deployed, and the security policy on each folder was confirmed. Look for **Successfully checked that the SRS web service is healthy on server** after the last line of security policy confirmations.  
  
##  <a name="BKMK_Certificate"></a> Configure a self-signed certificate for Configuration Manager console computers  
 There are many options for you to author SQL Server Reporting Services reports. When you create or edit reports in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] opens Report Builder to use as the authoring environment. Regardless of how you author your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports, a self-signed certificate is required for server authentication to the site database server. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically installs the certificate on the site server and the computers with the SMS Provider installed. Therefore, you can create or edit reports from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console when it runs from one of these computers. However, when you create or modify reports from a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console that is installed on a different computer, you must export the certificate from the site server and then add it to the **Trusted People** certificate store on the computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
> [!NOTE]  
>  For more information about other report authoring environments for SQL Server Reporting Services, see [Comparing Report Authoring Environments](http://go.microsoft.com/fwlink/p/?LinkId=242805) in the SQL Server 2008 Books Online.  
  
 Use the following procedure as an example of how to transfer a copy of the self-signed certificate from the site server to another computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console when both computers run Windows Server 2008 R2. If you cannot follow this procedure because you have a different operating system version, refer to your operating system documentation for the equivalent procedure.  
  
#### To transfer a copy of self-signed certificate from the site server to another computer  
  
1.  Perform the following steps on the site server to export the self-signed certificate:  
  
    1.  Click **Start**, click **Run**, and type **mmc.exe**. In the empty console, click **File**, and then click **Add/Remove Snap-in**.  
  
    2.  In the **Add or Remove Snap-ins** dialog box, select **Certificates** from the list of **Available snap-ins**, and then click **Add**.  
  
    3.  In the **Certificate snap-in** dialog box, select **Computer account**, and then click **Next**.  
  
    4.  In the **Select Computer** dialog box, ensure that **Local computer: (the computer this console is running on)** is selected, and then click **Finish**.  
  
    5.  In the **Add or Remove Snap-ins** dialog box, click **OK**.  
  
    6.  In the console, expand **Certificates (Local Computer)**, expand **Trusted People**, and select **Certificates**.  
  
    7.  Right-click the certificate with the friendly name of <*FQDN of site server*>, click **All Tasks**, and then select **Export**.  
  
    8.  Complete the **Certificate Export Wizard** by using the default options and save the certificate with the **.cer** file name extension.  
  
2.  Perform the following steps on the computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to add the self-signed certificate to the Trusted People certificate store:  
  
    1.  Repeat the preceding steps 1.a through 1.e to configure the **Certificate** snap-in MMC on the management point computer.  
  
    2.  In the console, expand **Certificates (Local Computer)**, expand **Trusted People**, right-click **Certificates**, select **All Tasks**, and then select **Import** to start the **Certificate Import Wizard**.  
  
    3.  On the **File to Import** page, select the certificate saved in step 1.h, and then click **Next**.  
  
    4.  On the **Certificate Store** page, select **Place all certificates in the following store**, with the **Certificate store** set to **Trusted People**, and then click **Next**.  
  
    5.  Click **Finish** to close the wizard and complete the certificate configuration on the computer.  
  
##  <a name="BKMK_ModifyReportingServicesPoint"></a> Modify Reporting Services Point settings  
 After the reporting services point is installed, you can modify the site database connection and authentication settings in the reporting services point properties. Use the following procedure to modify the reporting services point settings.  
  
#### To modify reporting services point settings  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, and then click **Servers and Site System Roles** to list the site systems.  
  
    > [!TIP]  
    >  To list only site systems that host the reporting services point site role, right-click **Servers and Site System Roles** to select **Reporting services point**.  
  
3.  Select the site system that hosts the reporting services point on which you want to modify settings, and then select **Reporting service point** in **Site System Roles**.  
  
4.  On the **Site Role** tab, in the **Properties** group, click **Properties**.  
  
5.  On the **Reporting Services Point Properties** dialog box, you can modify the following settings:  
  
    -   **Site database server name**: Specify the name of the server that hosts the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database. Typically, the wizard automatically retrieves the fully qualified domain name (FQDN) for the server. To specify a database instance, use the format <*Server Name*>\\<*Instance Name*>.  
  
    -   **Database name**: Specify the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] site database name, and then click **Verify** to confirm that the wizard has access to the site database.  
  
        > [!IMPORTANT]  
        >  The user account that is creating the reporting services point must have Read access to the site database. If the connection test fails, a red warning icon appears. Move the cursor over this icon to read details of the failure. Correct the failure, and then click **Test** again.  
  
    -   **User account**: Click **Set**, and then select an account that is used when SQL Server Reporting Services on the reporting services point connects to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database to retrieve the data that are displayed in a report. Select **Existing account** to specify a Windows user account that has existing [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] rights or select **New account** to specify a Windows user account that currently does not have rights in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically grants the specified user account access to the site database. The account is displayed as the **ConfigMgr SRS reporting point** account in the **Accounts** subfolder of the **Security** node in the **Administration** workspace.  
  
         The specified Windows user account and password are encrypted and stored in the Reporting Services database. Reporting Services retrieves the data for reports from the site database by using this account and password.  
  
        > [!IMPORTANT]  
        >  When the site database is on a remote site system, the account that you specify must have the **Log on Locally** permission for the computer.  
  
6.  Click **OK** to save the changes and exit the dialog box.  
  
## Upgrading SQL Server  
 After you upgrade SQL Server, and SQL Server Reporting Services that is used as the data source for a reporting services point, you might experience errors when you run or edit reports from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. For reporting to work properly from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you must remove the reporting services point site system role for the site and reinstall it. However, after the upgrade you can continue to run and edit reports successfully from an Internet browser.  
  
##  <a name="BKMK_ConfigureReportOptions"></a> Configure report options  
 Use the report options for a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site to select the default reporting services point that is used to manage your reports. Although you can have more than one reporting services point at a site, only the default report server selected in report options is used to manage reports. Use the following procedure to configure report options for your site.  
  
#### To configure report options  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the **Monitoring** workspace, expand **Reporting**, and then click **Reports**.  
  
3.  On the **Home** tab, in the **Settings** group, click **Report Options**.  
  
4.  Select the default report server in the list, and then click **OK**. If no reporting services points are listed in the list, verify that you have a reporting services point successfully installed and configured in the site.  
  
## See Also  
 [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md)