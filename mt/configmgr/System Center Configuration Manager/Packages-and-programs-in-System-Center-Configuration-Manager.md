---
title: "Packages and programs in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-04-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: caad0507-9913-415a-b13d-d36f8f0a1b80
caps.latest.revision: 8
caps.handback.revision: 0
author: barlanmsft
---
# Packages and programs in System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] continues to support packages and programs that were used in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007. A deployment that uses packages and programs might be more suitable than a deployment that uses an application when you deploy any of the following:  
  
 Packages and programs can be used to deploy applications to Windows PCs and Linux and UNIX servers.  
  
-   Scripts that do not install an application on a computer, such as a script to defragment the computer disk drive.  
  
-   “One-off” scripts that do not need to be continually monitored.  
  
-   Scripts that run on a recurring schedule and cannot use global evaluation.  
  
> [!TIP]  
>  You must use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] packages and programs to deploy software to clients that run Linux and UNIX. For more information, see [Creating Linux and UNIX server applications with System Center Configuration Manager](../System Center Configuration Manager/Creating-Linux-and-UNIX-server-applications-with-System-Center-Configuration-Manager.md).  
  
 When you migrate packages from an earlier version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can migrate existing packages and deploy them in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. After migration is complete, the packages appear in the **Packages** node in the **Software Library** workspace. You can modify and deploy these packages in the same way as you did by using software distribution. The **Import Package from Definition Wizard** remains in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to import legacy packages. Advertisements are converted to deployments when they are migrated from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy.  
  
> [!NOTE]  
>  You can use Microsoft System Center Configuration Manager Package Conversion Manager to convert packages and programs into [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] applications.  
>   
>  For more information, see [Configuration Manager Package Conversion Manager](https://technet.microsoft.com/library/hh531519.aspx).  
  
 Packages can use some new features of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], including distribution point groups and monitoring. Microsoft Application Virtualization (App-V) applications cannot be distributed by using packages and programs in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. To distribute virtual applications, you must create these as [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] applications.  
  
 Visit one of the following sections for help creating, deploying, monitoring, and managing [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] packages and programs:  
  
-   [How to create packages and programs](#BKMK_create)  
  
-   [How to deploy packages and programs](#BKMK_Deploy)  
  
-   [How to monitor packages and programs](#BKMK_Monitor)  
  
-   [How to manage packages and programs](#BKMK_Manage)  
  
##  <a name="BKMK_create"></a> How to create packages and programs  
 Use one of these procedures to help you create, or import packages and programs.  
  
#### Create a package and program using the Create Package and Program wizard  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Application Management**, and then click **Packages**.  
  
3.  In the **Home** tab, in the **Create** group, click **Create Package**.  
  
4.  On the **Package** page of the Create Package and Program Wizard, specify the following information:  
  
    -   **Name** - Specify a name for the package with a maximum of 50 characters.  
  
    -   **Description** - Optionally specify a description for this package with a maximum of 128 characters.  
  
    -   **Manufacturer** - Optionally specify a manufacturer name to help you identify the package in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. This name can be a maximum of 32 characters.  
  
    -   **Language** - Optionally specify the language version of the package with a maximum of 32 characters.  
  
    -   **Version** - Optionally specify a version number for the package with a maximum of 32 characters.  
  
    -   **This package contains source files** - This setting indicates whether the package requires source files to be present on client devices. By default, this check box is cleared and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not use distribution points for the package. When this check box is selected, distribution points are used.  
  
    -   **Source folder** -  If the package contains source files, click **Browse** to open the **Set Source Folder** dialog box and specify the location of the source files for the package.  
  
        > [!NOTE]  
        >  The computer account of the site server must have read access permissions to the source folder that you specify.  
  
5.  On the **Program Type** page of the Create Package and Program Wizard, select the type of program to create, and then click **Next**. You can create a program for a computer or device, or you can skip this step and create a program later.  
  
    > [!TIP]  
    >  To create a new program for an existing package, select the package, and then, in the **Home** tab, in the **Package** group, click **Create Program** to open the Create Program Wizard.  
  
6.  Use one of the following procedures to create a standard program or a device program.  
  
    ###### To create a standard program  
  
    1.  On the **Program Type** page of the **Create Package and Program Wizard**, select **Standard Program**, and then click **Next**.  
  
    2.  On the **Standard Program** page of the Wizard, specify the following information:  
  
        -   **Name:** Specify a name for the program with a maximum of 50 characters.  
  
            > [!NOTE]  
            >  The program name must be unique within a package. After you create a program, you cannot modify its name.  
  
        -   **Command Line** - Enter the command line to be used to start this program, or click **Browse** to browse to the file location.  
  
             If a specified file name does not have an extension specified, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] attempts to use .com, .exe, and .bat as possible extensions.  
  
             When the program is run on a client, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] first searches for the command-line file name within the package,  searches next in the local Windows folder, and then searches in local *%path%*. If the file cannot be found, the program fails.  
  
        -   **Startup folder** - Optionally use this field to specify the folder from which the program runs, up to 127 characters. This folder can be an absolute path on the client or a path relative to the distribution point folder that contains the package.  
  
        -   **Run** - Specifies the mode in which the program will run on client computers. Select one of the following:  
  
            -   **Normal** - The program runs in the normal mode based on system and program defaults. This is the default mode.  
  
            -   **Minimized** – The program runs minimized on client devices. Users might see installation activity in the notification area or taskbar.  
  
            -   **Maximized** – The program runs maximized on client devices. Users will see all installation activity.  
  
            -   **Hidden** – The program runs hidden on client devices. Users will not see any installation activity.  
  
        -   **Program can run** - Specify whether the program can run only when a user is logged on, run only when no user is logged on, or run regardless of whether  a user is logged on to the client computer.  
  
        -   **Run mode** - Specify whether the program will run with administrative permissions or with the permissions of the currently logged on user.  
  
        -   **Allow users to view and interact with the program installation** - Use this setting, if available, to specify whether to allow users to interact with the program installation. This check box is available only when **Only when no user is logged on** or **Whether or not a user is logged on** is selected for **Program can run** and **Run with administrative rights** is selected for **Run mode**.  
  
        -   **Drive mode** - Specify information about how this program will runs on the network. Choose one of the following:  
  
            -   **Runs with UNC name** - Indicates that the program runs with a Universal Naming Convention (UNC) name. This is the default setting.  
  
            -   **Requires drive letter** - Indicates that the program requires a drive letter to fully qualify its location. For this setting, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can use any available drive letter on the client.  
  
            -   **Requires specific drive letter (example: Z:)** - Indicates that the program requires a specific drive letter that you specify to fully qualify its location. If the specified drive letter is already used on a client, the program does not run.  
  
        -   **Reconnect to distribution point at log on** - Use this check box to indicate  whether the client computer reconnects to the distribution point when the user logs on. By default, this check box is cleared.  
  
    3.  On the **Requirements** page of the Create Package and Program Wizard, specify the following information:  
  
        -   **Run another program first** – You can use this setting to identify a package and program that will be run before this package and program will be run.  
  
        -   **Platform requirements** – Select **This program can run on any platform** or select **This program can run only on specified platforms** and then choose the operating systems that clients must be running to be able to install the package and program.  
  
        -   **Estimated disk space** - Specify the amount of disk space that the software program requires to be able to run on the computer. This can be specified as **Unknown** (the default setting) or as a whole number greater than or equal to zero. If a value is specified, units for the value must also be specified.  
  
        -   **Maximum allowed run time (minutes)** - Specify the maximum time that the program is expected to run on the client computer. This can be specified as **Unknown** (the default setting) or as a whole number greater than zero.  
  
             By default, this value is set to 120 minutes.  
  
            > [!IMPORTANT]  
            >  If you are using maintenance windows for the collection on which this program is run, a conflict may occur if the **Maximum allowed run time** is longer than the scheduled maintenance window. However, if the maximum run time is set to **Unknown**, the program will start to run during the maintenance window and will continue to run as needed after the maintenance window is closed. If the user sets the maximum run time to a specific period that exceeds the length of any available maintenance window, then the program will not be run.  
  
             If the value is set as **Unknown**, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sets the maximum allowed run time as 12 hours (720 minutes).  
  
            > [!NOTE]  
            >  If the maximum run time (whether set by the user or as the default value) is exceeded, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will stop the program if **run with administrative rights** is selected and **Allow users to view and interact with the program installation** is not selected.  
  
    4.  Click **Next**.  
  
    ###### To create a device program  
  
    1.  On the **Program Type** page of the **Create Package and Program Wizard**, select **Program for device**, and then click **Next**.  
  
    2.  On the **Program for Device** page of the Wizard, specify the following information:  
  
        -   **Name** - Specify a name for the program with a maximum of 50 characters.  
  
            > [!NOTE]  
            >  The program name must be unique within a package. After you create a program, you cannot modify its name.  
  
        -   **Comment** - Optionally, specify a comment for this device program with a maximum of 127 characters.  
  
        -   **Download folder** - Specify the name of the folder on the Windows CE device in which the package source files will be stored. The default value is **\Temp\\**.  
  
        -   **Command Line** - Enter the command line to use to start this program, or click **Browse** to browse to the file location.  
  
        -   **Run command line in download folder** – Select this option to run the program from the previously specified download folder.  
  
        -   **Run command line from this folder** – Select this option to specify a different folder from which to run the program.  
  
    3.  On the **Requirements** page of the wizard, specify the following information:  
  
        -   **Estimated disk space** - Specify the amount of disk space required for the software. This will be displayed to users of mobile devices before they install the program.  
  
        -   **Download program** - Specify information regarding when this program can be downloaded to mobile devices. You can specify **As soon as possible**, **Only over a fast network**, or **Only when the device is docked**.  
  
        -   **Additional requirements** - Specify any additional requirements for this program. These will be displayed to users before they install the software. For example, you could notify users that they need to close all other applications before running the program.  
  
    4.  Click **Next**.  
  
7.  On the **Summary** page of the wizard, review the actions that will be taken, then complete the wizard.  
  
 Verify that the new package and program is displayed in the **Packages** node of the **Software Library** workspace.  
  
#### Create a package and program from a package definition file  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Application Management**, and then click **Packages**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Package from Definition**.  
  
4.  On the **Package Definition** page of the Create Package from Definition Wizard, choose an existing package definition file, or click **Browse** to open a new package definition file. After you have specified a new package definition file, select it from the **Package definition** list, and then click **Next**.  
  
5.  On the **Source Files** page of the wizard, specify information about any required source files for the package and program, and then click **Next**.  
  
6.  If the package requires source files, on the **Source Folder** page of the wizard, specify the location from which the source files are to be obtained, and then click **Next**.  
  
7.  On the **Summary** page of the wizard, review the actions that will be taken and then complete the wizard. The new package and program is displayed in the **Packages** node of the **Software Library** workspace.  
  
 For more information about package definition files, see [Information about the package definition file format](#BKMK_PDF) in this topic.  
  
##  <a name="BKMK_Deploy"></a> How to deploy packages and programs  
  
#### To deploy a package and program  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Application Management**, and then click **Packages**.  
  
3.  Select the package that you want to deploy, and then in the **Home** tab in the **Deployment** group, click **Deploy**.  
  
4.  On the **General** page of the Deploy Software Wizard, specify the name of the package and program that you want to deploy, the collection to which you want to deploy the package and program, and optional comments for the deployment.  
  
     Select **Use default distribution point groups associated to this collection** if you want to store the package content on the collections default distribution point group. If you did not associate the selected collection with a distribution point group, this option will be unavailable.  
  
5.  On the **Content** page of the wizard, click **Add**, and then select the distribution points or distribution point groups to which you want to deploy the content that is associated with this package and program.  
  
6.  On the **Deployment Settings** page of the Wizard, choose a purpose for this deployment, and specify options for wake-up packets, and metered connections:  
  
    -   **Purpose** - Choose from:  
  
        -   **Available** - If the application is deployed to a user, the user sees the published package and program in the Application Catalog and can request it on demand. If the package and program is deployed to a device, the user will see it in Software Center and can install it on demand.  
  
        -   **Required** - The package and program is deployed automatically, according to the configured schedule. However, a user can track the package and program deployment status and install it before the deadline by using Software Center.  
  
    -   **Send wake-up packets** – If the deployment purpose is set to **Required** and this option is selected, a wake-up packet will be sent to computers before the deployment is installed to wake the computer from sleep at the installation deadline time. Before you can use this option, computers must be configured for Wake On LAN.  
  
    -   Select **Allow clients on a metered Internet connection to download content after  the installation deadline, which might incur additional costs** if required.  
  
    > [!NOTE]  
    >  The **Pre-deploy software to the user's primary device** option is not available when you deploy a package and program.  
  
7.  On the **Scheduling** page of the wizard, configure when this package and program will be deployed or made available to client devices.  
  
     The options on this page will vary depending on whether the deployment action is set to **Available** or **Required**.  
  
8.  If the deployment purpose is set to **Required**, configure the rerun behavior for the program from the **Rerun behavior** drop-down list. Choose from the following options:  
  
    |Rerun behavior|More information|  
    |--------------------|----------------------|  
    |Never rerun deployed program|The program will not be rerun on the client, even if the program originally failed, or the program files are changed.|  
    |Always rerun program|The program will always be rerun on the client when the deployment is scheduled, even if the program has already successfully run. This can be useful when you use recurring deployments in which the program is updated, for example with antivirus software.|  
    |Rerun if failed previous attempt|The program will be rerun when the deployment is scheduled only if it failed on the previous run attempt.|  
    |Rerun if succeeded on previous attempt|The program will be rerun only if it previously ran successfully on the client. This is useful when you use recurring advertisements in which the program is routinely updated, and in which each update requires the previous update to be successfully installed.|  
  
9. On the **User Experience** page of the wizard, specify the following information:  
  
    -   **Allow users to run the program independently of assignments** – If enabled, users can install this software from Software Center regardless of any scheduled installation time.  
  
    -   **Software installation** – Allows the software to be installed outside of any configured maintenance windows.  
  
    -   **System restart (if required to complete the installation)** – If the software installation requires a device restart to complete, allow this to happen outside of any configured maintenance windows.  
  
    -   **Embedded Devices** - When you deploy packages and programs to Windows Embedded devices that are write filter enabled, you can specify to install the packages and programs on the temporary overlay and commit changes later, or commit the changes at the installation deadline or during a maintenance window. When you commit changes at the installation deadline or during a maintenance window, a restart is required and the changes persist on the device.  
  
        > [!NOTE]  
        >  When you deploy a package or program to a Windows Embedded device, make sure that the device is a member of a collection that has a configured maintenance window. For more information about how maintenance windows are used when you deploy packages and programs to Windows Embedded devices, see [Creating Windows Embedded applications with System Center Configuration Manager](../System Center Configuration Manager/Creating-Windows-Embedded-applications-with-System-Center-Configuration-Manager.md).  
  
10. On the **Distribution Points** page of the wizard, specify the following information:  
  
    -   **Deployment options** – Specify the actions that a client should take to run program content. You can specify behavior when the client is in a fast network boundary, or a slow or unreliable network boundary.  
  
    -   **Allow clients to share content with other clients on the same subnet** – Select this option to reduce load on the network by allowing clients to download content from other clients on the network that already downloaded and cached the content. This option utilizes Windows BranchCache and can be used on computers that run Windows Vista SP2 and later.  
  
    -   **Allow clients to use a fallback source location for content** – If enabled, clients can search other distribution points in the hierarchy for required content if this is not available on the specified distribution point or distribution point groups.  
  
11. On the **Summary** page of the wizard, review the actions that will be taken and then complete the wizard.  
  
     You can view the deployment in the **Deployments** node of the **Monitoring** workspace and in the details pane of the package deployment tab when you select the deployment. For more information, see [How to monitor packages and programs](#BKMK_Monitor) in this topic.  
  
> [!IMPORTANT]  
>  If you configured the option **Run program from distribution point** on the **Distribution Points** page of the Deploy Software Wizard, do not clear the option **Copy the content in this package to a package share on distribution points**, because this will make the package unavailable to run from distribution points.  
  
##  <a name="BKMK_Monitor"></a> How to monitor packages and programs  
 To monitor package and program deployments, you use the same procedures that you use to monitor applications as detailed in [Monitor applications with System Center Configuration Manager](../System Center Configuration Manager/Monitor-applications-with-System-Center-Configuration-Manager.md).  
  
 Packages and programs also includes a number of built-in reports, which allow you to monitor information about the deployment status of packages and programs. These reports have the report category of **Software Distribution – Packages and Programs** and **Software Distribution – Package and Program Deployment Status**.  
  
 For more information about how to configure reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_Manage"></a> How to manage packages and programs  
 In the **Software Library** workspace, expand **Application Management**, click **Packages**, select the package that you want to manage, and then select a management task from the following table:  
  
|Task|More information|  
|----------|----------------------|  
|**Create Prestage Content File**|Opens the Create Prestaged Content File Wizard that allows you to create a file that contains the package content that can be manually imported to another site. This is useful in situations where you have low network bandwidth between the site server and the distribution point.|  
|**Create Program**|Opens the Create Program Wizard that allows you to create a new program for this package.|  
|**Export**|Opens the Export Package Wizard that allows you to export the selected package and its content to a file.<br /><br /> For information about how to import packages and programs, see [How to create packages and programs](#BKMK_create) in this topic.|  
|**Deploy**|Opens the Deploy Software Wizard that allows you to deploy the selected package and program to a collection. For more information, see [How to deploy packages and programs](#BKMK_Deploy) in this topic.|  
|**Distribute Content**|Opens the Distribute Content Wizard that allows you to send the content that is associated with the package and program to selected distribution points or distribution point groups.|  
|**Update Distribution Points**|Updates distribution points with the latest content for the selected package and program.|  
  
##  <a name="BKMK_PDF"></a> Information about the package definition file format  
 Package definition files are scripts that you can use to help automate package and program creation with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. They provide all of the information that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] needs in order to create a package and program, except for the location of package source files. Each package definition file is an ASCII or UTF-8 text file following the .ini file format and containing the following described sections:  
  
-   [[PDF]](#BKMK_Address)  
  
-   [[Package Definition]](#BKMK_Pack)  
  
-   [[Program]](#BKMK_Prog)  
  
###  <a name="BKMK_Address"></a> [PDF]  
 This section identifies the file as a package definition file. It contains the following information:  
  
-   **Version**: This specifies the version of the package definition file format that is used by the file. This corresponds to the version of System Management Server (SMS) or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] for which it was written. This entry is required.  
  
###  <a name="BKMK_Pack"></a> [Package Definition]  
 This section of the package definition file specifies the properties of the package and program. It provides the following information:  
  
-   **Name**: The name of the package, up to 50 characters. This entry is required.  
  
-   **Version**: The version of the package, up to 32 characters. This entry is optional.  
  
-   **Icon**: Optionally, the file containing the icon to use for this package. If specified, this icon will replace the default package icon in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
-   **Publisher**: The publisher of the package, up to 32 characters. This entry is required.  
  
-   **Language**: The language version of the package, up to 32 characters. This entry is required.  
  
-   **Comment**: An optional comment about the package, up to 127 characters.  
  
-   **ContainsNoFiles**: This entry indicates whether or not a source is associated with the package.  
  
-   **Programs**: The programs defined for this package. Each program name corresponds to a **[Program]** section in this package definition file. This entry is required.  
  
     Example:  
  
     `Programs=Typical, Custom, Uninstall`  
  
-   **MIFFileName**: The name of the Management Information Format (MIF) file that contains the package status, up to 50 characters.  
  
-   **MIFName**: The name of the package (for MIF matching), up to 50 characters.  
  
-   **MIFVersion**: The version number of the package (for MIF matching), up to 32 characters.  
  
-   **MIFPublisher**: The software publisher of the package (for MIF matching), up to 32 characters.  
  
###  <a name="BKMK_Prog"></a> [Program]  
 For each program specified in the **Programs** entry in the **[Package Definition]** section, the package definition file must include a [Program] section that defines that program. Each Program section provides the following information:  
  
-   **Name**: The name of the program, up to 50 characters. This entry must be unique within a package. This name is used when defining advertisements. On client computers, the name of the program is shown in **Run Advertised Programs** in Control Panel. This entry is required.  
  
-   **Icon**: Optionally specifies the file containing the icon to use for this program. If specified, this icon will replace the default program icon in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and will be displayed on client computers when the program is advertised.  
  
-   **Comment**: An optional comment about the program, up to 127 characters.  
  
-   **CommandLine**: Specifies the command line for the program, up to 127 characters. The command is relative to the package source folder. This entry is required.  
  
-   **StartIn**: Specifies the working folder for the program, up to 127 characters. This entry can be an absolute path on the client computer or a path relative to the package source folder. This entry is required.  
  
-   **Run**: Specifies the program mode in which the program will run. You can specify **Minimized**, **Maximized**, or **Hidden**. If this entry is not included, the program will run in normal mode.  
  
-   **AfterRunning**: Specifies any special action that occurs after the program is successfully completed. Options available are **SMSRestart**, **ProgramRestart**, or **SMSLogoff**. If this entry is not included, the program will not run a special action.  
  
-   **EstimatedDiskSpace**: Specifies the amount of disk space that the software program requires to be able run on the computer. This can be specified as **Unknown** (the default setting) or as a whole number greater than or equal to zero. If a value is specified, the units for the value must also be specified.  
  
     Example:  
  
     `EstimatedDiskSpace=38MB`  
  
-   **EstimatedRunTime**: Specifies the estimated duration (in minutes) that the program is expected to run on the client computer. This can be specified as **Unknown** (the default setting) or as a whole number greater than zero.  
  
     Example:  
  
     `EstimatedRunTime=25`  
  
-   **SupportedClients**: Specifies the processors and operating systems on which this program will run. The specified platforms must be separated by commas. If this entry is not included, supported platform checking will be disabled for this program.  
  
-   **SupportedClientMinVersionX**, **SupportedClientMaxVersionX**: Specifies the beginning-to-ending range for version numbers for the operating systems specified in the **SupportedClients** entry.  
  
     Example:  
  
    ```  
    SupportedClients=Win NT (I386),Win NT (IA64),Win NT (x64)  
    Win NT (I386) MinVersion1=5.00.2195.4  
    Win NT (I386) MaxVersion1=5.00.2195.4  
    Win NT (I386) MinVersion2=5.10.2600.2  
    Win NT (I386) MaxVersion2=5.10.2600.2  
    Win NT (I386) MinVersion3=5.20.0000.0  
    Win NT (I386) MaxVersion3=5.20.9999.9999  
    Win NT (I386) MinVersion4=5.20.3790.0  
    Win NT (I386) MaxVersion4=5.20.3790.2  
    Win NT (I386) MinVersion5=6.00.0000.0  
    Win NT (I386) MaxVersion5=6.00.9999.9999  
    Win NT (IA64) MinVersion1=5.20.0000.0  
    Win NT (IA64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion1=5.20.0000.0  
    Win NT (x64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion2=5.20.3790.0  
    Win NT (x64) MaxVersion2=5.20.9999.9999  
    Win NT (x64) MinVersion3=5.20.3790.0  
    Win NT (x64) MaxVersion3=5.20.3790.2  
    Win NT (x64) MinVersion4=6.00.0000.0  
    Win NT (x64) MaxVersion4=6.00.9999.9999   
    ```  
  
-   **AdditionalProgramRequirements**: Optionally provide any other information or requirements for client computers, up to 127 characters.  
  
-   **CanRunWhen**: Specifies the user status that the program requires to be able run on the client computer. Available values are **UserLoggedOn**, **NoUserLoggedOn**, or **AnyUserStatus**. The default value is **UserLoggedOn**.  
  
-   **UserInputRequired**: Specifies whether the program requires interaction with the user. Available values are **True** or **False**. The default value is **True**. This entry is set to **False** if **CanRunWhen** is not set to **UserLoggedOn**.  
  
-   **AdminRightsRequired**: Specifies whether the program requires administrative credentials on the computer to be able to run. Available values are **True** or **False**. The default value is **False**. This entry is set to **True** if **CanRunWhen** is not set to **UserLoggedOn**.  
  
-   **UseInstallAccount**: Specifies whether the program uses the Client Software Installation Account when it runs on client computers. By default, this value is **False**. This value is also **False** if **CanRunWhen** is set to **UserLoggedOn**.  
  
-   **DriveLetterConnection**: Specifies whether the program requires a drive letter connection to the package files that are located on the distribution point. You can specify **True** or **False**. The default value is **False**, which allows the program to use a Universal Naming Convention (UNC) connection. When this value is set to **True**, the next available drive letter will be used (starting with Z: and proceeding backward).  
  
-   **SpecifyDrive**: Optionally, specifies a drive letter that the program requires to connect to the package files on the distribution point. This specification forces the use of the specified drive letter for client connections to distribution points.  
  
-   **ReconnectDriveAtLogon**: Specifies whether the computer reconnects to the distribution point when the user logs on. Available values are **True** or **False**. The default value is **False**.  
  
-   **DependentProgram**: Specifies a program in this package that must run before the current program. This entry uses the format **DependentProgram**=<**ProgramName>**, where **<ProgramName\>** is the **Name** entry for that program in the package definition file. If there are no dependent programs, leave this entry empty.  
  
     Example:  
  
     DependentProgram=Admin  
    DependentProgram=  
  
-   **Assignment**: Specifies how the program is assigned to users. This value can be: **FirstUser,** only the first user who logs on runs the program; or **EveryUser,** every user who logs on to the client runs the program. When **CanRunWhen** is not set to **UserLoggedOn**, this entry is set to **FirstUser**.  
  
-   **Disabled**: Specifies whether this program can be advertised to clients. Available values are **True** or **False**. The default value is **False**.  
  
## See Also  
 [Application management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Application-management-technical-reference-for-System-Center-Configuration-Manager.md)