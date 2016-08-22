---
title: "Get started with application management in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
caps.latest.revision: 18
author: barlanmsft
---
# Get started with application management in System Center Configuration Manager
In this topic, you'll learn the basics you need to know before you start working with [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] applications.  
  
> [!TIP]  
>  If you are already familiar with how to manage applications in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can feel free to skip this topic and move straight on to creating a sample application. See [Create and deploy an application with System Center Configuration Manager](../System Center Configuration Manager/Create-and-deploy-an-application-with-System-Center-Configuration-Manager.md).  
  
## What is an application?  
 Although ‘application’ is a widely used term in computing, in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], it means something different. Think of an application like a box. This box contains one or more sets of installation files for a software package  (known as a **deployment type**) plus instructions on how to deploy the software.  
  
 When the application is deployed to devices, **requirements** decide which deployment type is installed on the device.  
  
 Of course, there are a lot more things you can do with an application, and you'll learn about these as you read through this guide. The following table introduces some concepts you'll need to know before you start to dig deeper. You won't need all of these in every application you create:  
  
|||  
|-|-|  
|Concept|Description|  
|**Requirements**|In previous versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you would often create a collection containing the devices you wanted to deploy an application to. Although you can still do this, requirements reduce that need by allowing you to specify much more granular criteria by which an application will be installed.<br /><br /> For example, you can specify that an application can only install on devices that run Windows 10. Then, you can deploy the application to all of your devices, but it will only install on devices that run Windows 10.<br /><br /> [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] evaluates requirements to determine whether an application and any of its deployment types will be installed. Then it determines the correct deployment type by which to install an application. Every seven days, by default, the requirement rules are reevaluated to ensure compliance according to the client setting **Schedule re-evaluation for deployments**.<br /><br /> For details, see [Create and deploy an application with System Center Configuration Manager](../System Center Configuration Manager/Create-and-deploy-an-application-with-System-Center-Configuration-Manager.md).|  
|**Global conditions**|While requirements are used with a specific deployment type in a single application, you can also create global conditions which are a library of predefined requirements that you can use with any application and deployment type.<br /><br /> [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] contains a set of built-in global conditions and you can also create your own.<br /><br /> For details, see [How to create global conditions in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-global-conditions-in-System-Center-Configuration-Manager.md).|  
|**Simulated deployment**|Evaluates the requirements, detection method, and dependencies for an application and reports the results without actually installing the application.<br /><br /> For details, see [How to simulate application deployments with System Center Configuration Manager](../System Center Configuration Manager/How-to-simulate-application-deployments-with-System-Center-Configuration-Manager.md).|  
|**Deployment action**|Specifies whether you want to install, or uninstall (when supported) the application you are deploying.<br /><br /> For details, see [How to deploy applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-applications-with-System-Center-Configuration-Manager.md).|  
|**Deployment purpose**|Specifies whether the deployment app will  be **Required**, or **Available**.<br /><br /> **Required** means that the application is deployed automatically according to the configured schedule. However, a user can track the application deployment status if it is not hidden, and can install the application before the deadline by using the Software Center.<br /><br /> **Available** means that if the application is deployed to a user, the user sees the published application in Software Center, and can request it on demand.<br /><br /> For details, see [How to deploy applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-applications-with-System-Center-Configuration-Manager.md).|  
|**Revisions**|When you make revisions to an application or to a deployment type that is contained in an application, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] creates a new revision of the application. You can display the history of each application revision, view its properties, restore a previous revision of an application, or delete an old revision.<br /><br /> For details, see [Update and retire applications with System Center Configuration Manager](../System Center Configuration Manager/Update-and-retire-applications-with-System-Center-Configuration-Manager.md).|  
|**Detection method**|Detection methods are used to discover whether a deployed application is already installed. If the detection method indicates the application is installed, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not attempt to install it again.<br /><br /> For details, see [How to create applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-create-applications-with-System-Center-Configuration-Manager.md).|  
|**Dependencies**|Dependencies define one or more deployment types from another application that must be installed before a deployment type is installed. You can configure the dependent deployment types to be installed automatically before a deployment type is installed.<br /><br /> For details, see [How to create applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-create-applications-with-System-Center-Configuration-Manager.md).|  
|**Supersedence**|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] lets you  upgrade or replace existing applications by using a supersedence relationship. When you supersede an application, you can specify a new deployment type to replace the deployment type of the superseded application and also configure whether to upgrade or uninstall the superseded application before the superseding application is installed.<br /><br /> For details, see [How to create applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-create-applications-with-System-Center-Configuration-Manager.md).|  
|**User-centric management**|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] applications support user-centric management letting you can associate specific users with specific devices. Instead of having to remember the name of a user’s device, you can deploy apps to the user and to the device. This functionality can help you make sure that the most important apps are always available on each device that a specific user accesses. If a user acquires a new computer, you can automatically install the user’s apps on the device before they log on.<br /><br /> For details, see [Link users and devices with user device affinity in System Center Configuration Manager](../System Center Configuration Manager/Link-users-and-devices-with-user-device-affinity-in-System-Center-Configuration-Manager.md).|  
  
## What application types can you deploy?  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports deploying the following types of software:  
  
|Type|Requires device to be enrolled with Intune|  
|----------|------------------------------------------------|  
|Windows Installer (*.msi file)|No|  
|Windows app package (*.appx, \*.appxbundle)|No|  
|Windows app package (in the Windows Store)|No|  
|Microsoft Application Virtualization 4|No|  
|Microsoft Application Virtualization  5|No|  
|Windows Phone app package (*.xap file)|Yes|  
|Windows Phone app package (in the Windows Phone Store)|Yes|  
|Windows Mobile Cabinet|No|  
|App Package for iOS (*.ipa file)|Yes|  
|App Package for Android (*.apk file)|Yes|  
|App Package for Android on Google Play|Yes|  
|Mac OS X|No|  
|Web Application|Only when deploying to iOS, Android, Windows Phone, and enrolled Windows PCs|  
|Windows Installer through MDM|Yes|  
  
## State-based applications  
 Applications in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] support state-based monitoring, by which you can track the last application deployment state for users and devices. The state messages display information about individual devices. For example, if an application is deployed to a collection of users, you can view the compliance state of the deployment and the deployment purpose in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. You can monitor the deployment of all software by using the **Monitoring** workspace in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. Software deployments include software updates, compliance settings, applications, task sequences, and packages and programs. For more information, see [Monitor applications with System Center Configuration Manager](../System Center Configuration Manager/Monitor-applications-with-System-Center-Configuration-Manager.md).  
  
 Application deployments are regularly re-evaluated by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For example:  
  
-   A deployed application is uninstalled by the end-user. At the next evaluation cycle, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] detects that the application is not present and reinstalls it.  
  
-   An application was not installed on a device because it failed to meet the requirements. Later, a change is made to the device and it now meets the requirements. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] detects this change and the application is installed.  
  
 You can configure the re-evaluation interval for application deployments by using the **Schedule re-evaluation for deployments** client setting. For more information, see [About client settings in System Center Configuration Manager](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md).  
  
## Get started creating an application  
 If you want to jump right in and start to create an application, you'll find a walkthrough for creating a simple application in the [Create and deploy an application with System Center Configuration Manager](../System Center Configuration Manager/Create-and-deploy-an-application-with-System-Center-Configuration-Manager.md) topic.  
  
 If you are familiar with the basics and looking for more detailed reference information about all the options available to you, start from [Application management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Application-management-technical-reference-for-System-Center-Configuration-Manager.md).  
  
## Software Center and the Application Catalog  
 In previous versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], Software Center was used to install and schedule software installations, configure remote control settings, and configure power management settings. Users could connect to the Application Catalog to browse for, and request software, configure some preference settings, and remotely wipe their mobile devices.  
  
 While these settings are still available in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], a new version of Software Center is now available that allows you to browse for applications without having to use  the Application Catalog, which requires  a Silverlight enabled web browser. However the Application Catalog website point and Application Catalog web service point site system roles are still required for user-available apps to appear in Software Center.  
  
 For more information, see [Plan for and configure application management in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-and-configure-application-management-in-System-Center-Configuration-Manager.md).  
  
## Using Configuration Manager packages and programs  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] continues to support packages and programs that were used in previous versions of the product. A deployment that uses packages and programs might be more suitable than a deployment that uses an application when you deploy any of the following:  
  
-   Scripts that do not install an application on a computer, such as a script to defragment the computer disk drive  
  
-   “One-off” scripts that do not need to be continually monitored  
  
-   Scripts that run on a recurring schedule and cannot use global evaluation  
  
 For more information, see [Packages and programs in System Center Configuration Manager](../System Center Configuration Manager/Packages-and-programs-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Deploy and manage applications with System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-applications-with-System-Center-Configuration-Manager.md)