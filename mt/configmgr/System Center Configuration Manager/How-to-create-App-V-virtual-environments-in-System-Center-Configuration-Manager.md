---
title: "How to create App-V virtual environments in System Center Configuration Manager"
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
ms.assetid: b6b86078-fcc4-46cf-87d6-4b52b914b712
caps.latest.revision: 6
caps.handback.revision: 0
author: barlanmsft
---
# How to create App-V virtual environments in System Center Configuration Manager
Microsoft Application Virtualization (App-V) virtual environments in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] enable deployed virtual applications to share the same file system and registry on client computers. This means that unlike standard virtual applications, these applications can share data with each other. Virtual environments are created or modified on client computers when the application is installed or when clients next evaluate their installed applications. You can order these applications so that when multiple applications try to modify a file system or registry value, the application with the highest order takes priority.  
  
> [!IMPORTANT]  
>  Do not rely upon App-V virtual environments to provide security protection, for example, from malware.  
  
 Use the following procedure to create App-V virtual environments in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
### To create an App-V virtual environment  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Application Management** and then click **App-V Virtual Environments**.  
  
3.  In the **Home** tab, in the **Create** group, click **Create Virtual Environment**.  
  
4.  In the **Create Virtual Environment** dialog box, specify the following information:  
  
    -   **Name** - Specify a unique name for the virtual environment with a maximum of 128 characters.  
  
    -   **Description** - Optionally specify a description for the virtual environment.  
  
5.  Click **Add** to add a new deployment type to the virtual environment. You must add at least one deployment type.  
  
6.  In the **Add Applications** dialog box, specify a **Group name** of up to 128 characters that you will use to refer to this group of applications that you add to the virtual environment.  
  
7.  Click **Add**, select the App-V 5 applications and deployment types that you want to add to the group and then click **OK**.  
  
8.  In the **Add Applications** dialog box, you can click **Increase Order** or **Decrease Order** to specify which application will take priority if multiple applications attempt to modify file system or registry settings in the same virtual environment.  
  
9. Click **OK** to return to the **Create Virtual Environment** dialog box.  
  
10. When you have finished adding groups, click **OK** to create the virtual environment. The new virtual environment is displayed in the **App-V Virtual Environments** node of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. You can monitor the status of your virtual environments by using the report **App-V Virtual Environment Status**.  
  
    > [!NOTE]  
    >  The virtual environment will be added or modified on client computers when the application is installed or when the client next evaluates installed applications.  
  
## See Also  
 [Application management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Application-management-technical-reference-for-System-Center-Configuration-Manager.md)