---
title: "Deploying App-V virtual applications with System Center Configuration Manager"
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
ms.assetid: ddcad9f2-a542-4079-83ca-007d7cb44995
caps.latest.revision: 11
caps.handback.revision: 0
author: barlanmsft
---
# Deploying App-V virtual applications with System Center Configuration Manager
In addition to the other [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] requirements and procedures for creating an application, you must also take the following considerations into account when you create and deploy virtual applications.  
  
 Use the information in the following sections to help you plan to integrate your App-V environment with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   [General considerations](#BKMK_General)  
  
-   [Supported App-V versions](#BKMK_Supp)  
  
-   [Steps to manage App-V virtual applications](#BKMK_Steps)  
  
-   [Configuration Manager virtual application delivery methods](#BKMK_Delivery)  
  
-   [Migrating from an App-V infrastructure to a Configuration Manager and App-V infrastructure](#BKMK_Migrate)  
  
-   [Migrating App-V 5 connection groups to Configuration Manager virtual environments](#BKMK_Connection)  
  
-   [Dynamic Suite Composition in App-V 4.6](#BKMK_DSC)  
  
-   [Converting App-V 4.6 applications to App-V 5 applications](#BKMK_Convert)  
  
-   [User and deployment configuration files](#BKMK_Config)  
  
-   [App-V local interaction](#BKMK_Interact)  
  
-   [App-V 5 Shared Content Store](#BKMK_SCS)  
  
-   [Monitoring virtual applications](#BKMK_Monitor)  
  
##  <a name="BKMK_General"></a> General considerations  
 You can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to install and manage virtual applications as deployment types in an application. When you do this, the following considerations apply:  
  
 When you use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to manage virtual applications, you gain the following benefits:  
  
-   Use a single management infrastructure  
  
-   Scalability, deployment, and content distribution features, such as collections and user device affinity  
  
-   Take advantage of the advanced application management features that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides  
  
-   Use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] features, such as operating system deployment, software and hardware inventory, software metering, and Asset Intelligence to support virtual applications  
  
 For more information about how to create and sequence applications with App-V, see [Application Virtualization](https://technet.microsoft.com/library/cc843848.aspx) in the TechNet Library.  
  
 To deploy virtual applications to computers, you must have the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client and App-V Client installed on your computers. Client devices can include desktop and portable computers, and Virtual Desktop Infrastructure (VDI) clients. The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and App-V Client software work together to deliver, locate, and launch virtual application packages. The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client manages the delivery of virtual application packages to the App-V Client. The App-V Client runs the virtual application on the client.  
  
-   To deploy a virtual application, you must first create the virtual application by using the App-V Application Virtualization Sequencer. The sequencer monitors the installation and setup process for an application and records the information that is needed for the application to run in a virtual environment. You can also use the sequencer to configure which files and configurations apply to all users and which configurations users can customize.  
  
-   When you sequence an application, you must save the package to a location that can be accessed by Configuration Manager. You can then create an application deployment that contains this virtual application.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support use of the shared read-only cache feature of App-V.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the shared content store feature in App-V 5.  
  
-   When you create a deployment type for a virtual application, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] creates the deployment type by using the contents of the application manifest file. This is an XML file that contains information about the virtual application. Additionally, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] creates requirements for the deployment type based on the contents of the App-V .osd file that contains information about the supported operating systems for the virtual application.  
  
-   To deploy virtual applications in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], client computers must have at minimum the App-V 4.6 SP1 or a later version of the client installed.  
  
-   Additionally, before you can successfully deploy virtual applications, you must update the App-V client with the hotfix described in the Knowledge Base article [2645225](https://support.microsoft.com/kb/2645225).  
  
-   When you use connection groups in Microsoft Application Virtualization 5.0, your deployed virtual applications can share the same file system and registry on client computers. Unlike standard virtual applications, these applications can share data with one another. Additionally, connection groups preserve user settings for the applications that they contain. App-V virtual environments in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] are used to configure connection groups on client computers. Virtual environments are created or changed on client computers when the application is installed or when clients next evaluate their installed applications. You can prioritize these applications so that when multiple applications try to change a file system or registry value, the application that has the highest priority takes precedence. For more information, see [How to create App-V virtual environments in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-App-V-virtual-environments-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_Supp"></a> Supported App-V versions  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the following versions of App-V:  
  
-   **App-V 4.6:** To use virtual applications in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], client computers must have the App-V 4.6 SP1, App-V 4.6 SP2, or App-V 4.6 SP3 client installed.  
  
     You must also update the App-V 4.6 SP1 client with the hotfix that is described in the Knowledge Base article [2645225](http://go.microsoft.com/fwlink/p/?LinkId=237322) before you can successfully deploy virtual applications.  
  
-   **App-V 5, App-V 5.0 SP1, App-V 5.0 SP2, App-V 5.0 SP3, and App-V 5.1:** For App-V 5.0 SP2, you must install [Hotfix Package 5](https://support.microsoft.com/en-us/kb/2963211) or use App-V 5.0 SP3.  
  
##  <a name="BKMK_Steps"></a> Steps to manage App-V virtual applications  
 To manage App-V virtual applications, complete the following steps:  
  
-   **Sequencing** - Sequencing is the process of converting an application into a virtual application by using the App-V Sequencer.  
  
-   **Create [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] applications** – Use the Create Deployment Type Wizard to import the sequenced application into a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] deployment type that you can then add to an application. You can also create virtual environments that allow multiple virtual applications to share settings.  
  
-   **Distribution** – Distribution is the process of making App-V applications available on [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] distribution points.  
  
-   **Deployment** – Deployment is the process of making the application available on client computers. This is referred to as streaming in an App-V full infrastructure. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides two options for the deployment of virtual applications: **streaming** and **download and execute**.  
  
##  <a name="BKMK_Delivery"></a> Configuration Manager virtual application delivery methods  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports two methods for delivery of virtual applications to clients: streaming delivery and local delivery (download and execute):  
  
-   **Streaming delivery**  
  
     When you use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to manage the App-V client, it supports the streaming of virtual applications through HTTP or HTTPS from a distribution point. Streaming through HTTP or HTTPS is enabled by default and is configured in the distribution point properties dialog box. When you deploy a virtual application to client computers and a user runs the virtual application, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client contacts a management point to determine which distribution point to use; then, the application is streamed from the distribution point.  
  
-   **Local delivery (download and execute)**  
  
     When you use this delivery method, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client first downloads the entire virtual application package into the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client cache, and then it instructs the App-V Client to stream the application from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cache into the App-V cache. If you deploy a virtual application to client computers and its content is not in the App-V cache, the App-V Client streams the application content from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client cache into the App-V cache, and then runs the application. After the application runs successfully, you can configure the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client to delete any older versions of the package at the next deletion cycle, or to persist them in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client cache.  
  
 When you decide which [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] virtual application delivery method to use, compare the reduced disk space requirement for streaming delivery against the guaranteed availability of App-V applications by using local delivery. The increased client disk space that is required for local delivery might be preferable to streaming delivery so that users always have the application available from any location.  
  
 Use the information in the following tables to help you choose the best delivery method.  
  
 **Streaming delivery**  
  
|Advantages|Disadvantages|  
|----------------|-------------------|  
|This method uses standard network protocols to stream package content from distribution points.<br /><br /> Program shortcuts for virtual applications invoke a connection to the distribution point, so the virtual application delivery is on demand.<br /><br /> This method works well for clients with high-bandwidth connections to the distribution points.<br /><br /> Updated virtual applications distributed throughout the enterprise are available as clients receive policy that informs them that the current version is superseded and they download only the changes from the previous version.<br /><br /> Access permissions are defined at the distribution point to prevent users from accessing unauthorized applications or packages.|Virtual applications are not streamed until the user runs the application for the first time. In this scenario, a user might receive program shortcuts for virtual applications and then disconnect from the network before running the virtual applications for the first time. If the user tries to run the virtual application while the client is offline, the user sees an error and will not be able to run the virtualized application because a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] distribution point is not available to stream the application. The application will be unavailable until the user reconnects to the network and runs the application.<br /><br /> To avoid this, you can use the local delivery method for virtual application delivery to clients, or you can enable the Internet-based client management for streaming delivery.|  
  
 **Local delivery**  
  
|Advantages|Disadvantages|  
|----------------|-------------------|  
|The standard distribution point functionality is used to download the package by using Background Intelligent Transfer Service (BITS).<br /><br /> Virtual application package contents are delivered locally to the client, which means that users can run them when their computer is not connected to the network.<br /><br /> This method is suitable for slow or unreliable network connections and for computers that only occasionally connect to the network.<br /><br /> [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses Remote Differential Compression (RDC) to send to clients only the bytes within the files that have changed when virtual application package content is updated. The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client uses RDC to build a new version of a virtual application package based on the current version of the package and any changes sent to the client.<br /><br /> This method provides application resiliency for mobile users or disconnected users. Administrators can choose to persist the package in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cache after delivery if the virtual application was deployed with an Install action. The package in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client cache serves as a local, reliable streaming source for the App-V Client to pull the package into its cache.|Disk space equaling up to twice the size of the virtual application package is required on the client when the virtual application is persisted in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cache.|  
  
 You can also preinstall virtual applications on a computer and then create an image of that computer for deployment to other computers. However, if the virtual application package was created at a different site, then the binary delta replication will not be used to download updates to the application. This option can be useful in a virtual desktop infrastructure when you want applications to be available immediately instead of downloading the applications after the user logs on.  
  
##  <a name="BKMK_Migrate"></a> Migrating from an App-V infrastructure to a Configuration Manager and App-V infrastructure  
 Use the following table to help you plan a migration from an existing App-V infrastructure to virtual application management with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
|Step|More information|  
|----------|----------------------|  
|Examine your current virtual applications to choose the applications that you want to migrate into your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure.|No additional information.|  
|Evaluate the users and devices to which the virtual applications will be deployed.|Create [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collections to group together the users and devices to which you want to deploy the virtual applications. For more information, see [Collections technical reference for System Center Configuration Manager](../System Center Configuration Manager/Collections-technical-reference-for-System-Center-Configuration-Manager.md).|  
|Migrate App-V 5 connection groups to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] virtual environments.|For more information, see the [Migrating App-V 5 connection groups to Configuration Manager virtual environments](#BKMK_Connection) section in this topic.|  
|Investigate to find out if any of your virtual applications exist as full applications in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure.|For easier management, you can add the virtual application as a new deployment type to the existing full application. For more information about how to create deployment types, see [How to create applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-create-applications-with-System-Center-Configuration-Manager.md).|  
|Create applications to replace your existing App-V packages.|For more information about how to create [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] applications, see [Get started with application management in System Center Configuration Manager](../System Center Configuration Manager/Get-started-with-application-management-in-System-Center-Configuration-Manager.md) and [How to create applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-create-applications-with-System-Center-Configuration-Manager.md).|  
|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] begins to manage virtual applications on a client after the first deployment of a virtual application. After this, all App-V applications on the computer must be managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].|No additional information.|  
|Distribute the content to the appropriate distribution points to enable local delivery of applications.|For more information, see [Manage content and content infrastructure for System Center Configuration Manager](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md).|  
|Deploy the application to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients.<br /><br /> If the App-V application was created with an earlier version of the Sequencer that does not create a manifest XML file, you can open it and save it in a newer version of the Sequencer to create the file. This file is required to deploy virtual applications with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].<br /><br /> App-V supports the virtual application packages that are created with the SoftGrid 4.1 SP1 or 4.2 versions of the Sequencer.<br /><br /> If the applications were previously installed locally, you must uninstall them before you deploy a virtual version of the application.|For more information, see [How to deploy applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-applications-with-System-Center-Configuration-Manager.md).|  
|[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] no longer supports using packages and programs that contain virtual applications. When you migrate from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] converts these packages into applications.<br /><br /> [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 advertisements are converted into the following deployment types:<br /><br /> - Migrating App-V packages with no advertisement:  One deployment type that uses the default deployment type settings.<br /><br /> - Migrating App-V packages with one advertisement: One deployment type that uses the same settings as the <br />                [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 advertisement.<br /><br /> - Migrating App-V packages with multiple advertisements: A deployment type for each <br />                [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 advertisement, that uses the settings for that advertisement.|For more information, see [Planning for the migration of Configuration Manager objects to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-the-migration-of-Configuration-Manager-objects-to-System-Center-Configuration-Manager.md).|  
  
##  <a name="BKMK_Connection"></a> Migrating App-V 5 connection groups to Configuration Manager virtual environments  
 App-V virtual environments in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] allow virtual applications that you have deployed to share the same file system and registry on client computers. This means that unlike standard virtual applications, these applications can share data with each other. Virtual environments are created or modified on client computers when the application is installed or when clients next evaluate their installed applications. Virtual environments are similar to connection groups in stand-alone App-V 5.  
  
 When you migrate connection groups from stand-alone App-V 5 to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] virtual environments, you must ensure that the connection groups that already exist on client computers are managed correctly by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], and that the user's environment within those connection groups is preserved.  
  
 Use the following procedure to help you successfully convert App-V 5 connection groups into [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] virtual environments.  
  
#### To convert App-V 5 connection groups to Configuration Manager virtual environments  
  
1.  Create [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] applications for all applications that existed in App-V.  
  
2.  Deploy the applications to users or devices with a deployment purpose of **Required**. Deployments to users must be deployed to the same users who used the application in App-V, and deployments to computers must be deployed to the same computers that had the application in App-V.  
  
3.  After the deployment is completed, create virtual environments that match the connection groups that are published in stand-alone App-V. The virtual environment must contain the same packages, specifically, App-V 5 deployment types, in the same order.  
  
     For information about how to create an App-V virtual environment, see [How to create App-V virtual environments in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-App-V-virtual-environments-in-System-Center-Configuration-Manager.md).  
  
 Alternatively, you can delete all connection groups from the App-V Client before you begin to deploy applications with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. However, any settings that users might have saved in App-V connection groups will be lost.  
  
##  <a name="BKMK_DSC"></a> Dynamic Suite Composition in App-V 4.6  
 Dynamic Suite Composition is a feature that provides the ability to define one virtual application package as having a dependency on another virtual application package. When the application is run, the App-V Client hosts the primary package and the dependent package in the same virtual environment for the application.  
  
 To use this feature with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], both packages must be deployed and registered with the App-V Client. To ensure that dependent package content is hosted locally on the client computer, configure the application deployment for local delivery (download and execute).  
  
 For more information about App-V Dynamic Suite Composition, see your App-V documentation.  
  
##  <a name="BKMK_Convert"></a> Converting App-V 4.6 applications to App-V 5 applications  
 The application package format has changed between App-V 4.6 and App-V 5. Applications that have been sequenced by using App-V 4.6 are no longer supported. However, App-V 5 has a package converter tool that you can use to convert applications. For more information, see your [App-V 5 documentation](http://technet.microsoft.com/library/jj713472.aspx).  
  
 Use the following steps to convert App-V 4.6 applications to App-V 5 applications:  
  
1.  Convert or re-sequence the App-V 4.6 packages into the App-V 5 format.  
  
2.  Deploy the App-V 5 client to computers in your hierarchy.  
  
3.  Create new applications that contain deployment types for your App-V 5 applications, and create supersedence rules to supersede the App-V 4.6 applications.  
  
4.  Create virtual environments as required.  
  
5.  Deploy the new App-V 5 applications to computers.  
  
##  <a name="BKMK_Config"></a> User and deployment configuration files  
 User and deployment configuration files contain settings that control how an application behaves. You can use these files to change application settings without re-sequencing the application.  
  
 A typical App-V 5 application might contain the following files:  
  
-   An application package (.appv) file.  
  
-   A user configuration file.  
  
-   A deployment configuration file.  
  
 The user configuration file contains settings that apply only to the logged on user. You could, for example, edit the configuration files to change the information about the application shortcut that will be deployed to users. You can also create a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] application with multiple deployment types, and each deployment type can contain a different user configuration file and use requirement rules to ensure that these are installed for the relevant users.  
  
 The deployment configuration file contains settings that apply to the computer, such as registry settings. The file can also contain user settings, which will be applied to all users.  
  
 If you want to deploy App-V 5 virtual applications with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], all three files must be present in the same folder when you create the App-V 5 deployment type. If there are multiple files in the folder, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will use the most recent.  
  
 For more information, see your [App-V 5 documentation](http://technet.microsoft.com/library/jj713466.aspx).  
  
##  <a name="BKMK_Interact"></a> App-V local interaction  
 In some application deployment scenarios, applications are installed locally on client computers and other applications are deployed as virtual applications to the same client computer. By default, the applications that were locally installed cannot see or communicate directly with virtualized applications. This is the intended behavior of the application isolation that is provided by App-V. Local Interaction is a feature of the App-V Client that you can enable for each application to allow locally installed applications that run on a client computer to see and communicate with virtualized applications. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and App-V fully support local interaction.  
  
 For more information about the App-V Local Interaction feature, see your App-V documentation.  
  
##  <a name="BKMK_SCS"></a> App-V 5 Shared Content Store  
 The App-V 5 Shared Content Store feature is supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For more information, see [Planning for the App-V 5.0 Shared Content Store (SCS)](http://technet.microsoft.com/library/jj713431.aspx).  
  
##  <a name="BKMK_Monitor"></a> Monitoring virtual applications  
 Use the information in this section to plan how to monitor App-V applications in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
### Virtual application reports  
 You can use the following reports to monitor App-V in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] environment:  
  
|Report name|Description|  
|-----------------|-----------------|  
|App-V Virtual Environment Results|Displays information about a selected virtual environment that is in a specified state for a selected collection (App-V 5 only).|  
|App-V Virtual Environment Results For Asset|Displays information about a selected virtual environment for a specified asset and any deployment types for the selected virtual environment (App-V 5 only).|  
|App-V Virtual Environment Status|Displays compliance information for a selected virtual environment for a selected collected. The **Retained** column in this report displays the assets in which a virtual environment that was previously configured is no longer applicable, but it is retained to persist user settings in applications that run in the virtual environment (App-V 5 only).|  
|Computers with a specific virtual application|Displays a summary of computers that have the specified App-V shortcut that was created by the Application Virtualization Management Sequencer (App-V 4.6 only).|  
|Computers with a specific virtual application package|Displays a list of computers that have the specified App-V application package installed (App-V 4.6 only).|  
|Count all instances of virtual application packages|Displays a count of all detected App-V application packages (App-V 4.6 only).|  
|Count all instances of virtual applications|Displays a count of all detected App-V applications (App-V 4.6 only).|  
  
### Log files  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] records information about virtual application deployments in log files. For information about the log files that are used by virtual applications and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] application management, see [Log files in System Center Configuration Manager](../System Center Configuration Manager/Log-files-in-System-Center-Configuration-Manager.md).  
  
 Additionally, you can find logs for the App-V client in the following locations:  
  
-   Windows Vista, Windows 7, and Windows 8: **C:\ProgramData\Microsoft\Application Virtualization Client**  
  
## See Also  
 [Create and deploy an application with System Center Configuration Manager](../System Center Configuration Manager/Create-and-deploy-an-application-with-System-Center-Configuration-Manager.md)