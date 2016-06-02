---
title: Connect to a Remote Integration Services Server (SSIS Service)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
---
# Connect to a Remote Integration Services Server (SSIS Service)
    
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. Starting in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], you can manage objects such as packages on the Integration Services server.  
  
 Connecting to an instance of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] on a remote server, from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or another management application, requires a specific set of rights on the server for the users of the application.  
  
> [!IMPORTANT]  
>  To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service on that remote server. Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service so that [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] displays the packages that are stored on the remote server. For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](../Topic/Configuring%20the%20Integration%20Services%20Service%20\(SSIS%20Service\).md).  
  
## Connecting to Integration Services on a Remote Server  
  
#### To connect to Integration Services on a Remote Server  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
2.  Select **File**, **Connect Object Explorer** to display the **Connect to Server** dialog box.  
  
3.  Select **Integration Services** in the **Server type** list.  
  
4.  Type the name of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server in the **Server name** text box.  
  
    > [!NOTE]  
    >  The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is not instance\-specific. You connect to the service by using the name of the computer on which the Integration Services service is running.  
  
5.  Click **Connect**.  
  
> [!NOTE]  
>  The **Browse for Servers** dialog box does not display remote instances of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. In addition, the options available on the **Connection Options** tab of the **Connect to Server** dialog box, which is displayed by clicking the **Options** button, are not applicable to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] connections.  
  
## Eliminating the "Access Is Denied" Error  
 When a user without sufficient rights attempts to connect to an instance of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] on a remote server, the server responds with an "Access is denied" error message. You can avoid this error message by ensuring that users have the required DCOM permissions.  
  
#### To configure rights for remote users on Windows Server 2003 or Windows XP  
  
1.  If the user is not a member of the local Administrators group, add the user to the Distributed COM Users group. You can do this in the Computer Management MMC snap\-in accessed from the **Administrative Tools** menu.  
  
2.  Open Control Panel, double\-click **Administrative Tools,** and then double\-click **Component Services** to start the Component Services MMC snap\-in.  
  
3.  Expand the **Component Services** node in the left pane of the console. Expand the **Computers** node, expand **My Computer**, and then click the **DCOM Config** node.  
  
4.  Select the **DCOM Config** node, and then select SQL Server Integration Services 11.0 in the list of applications that can be configured.  
  
5.  Right\-click on SQL Server Integration Services 11.0 and select **Properties**.  
  
6.  In the **SQL Server Integration Services 11.0 Properties** dialog box, select the **Security** tab.  
  
7.  Under **Launch and Activation Permissions**, select **Customize**, then click **Edit** to open the **Launch Permission** dialog box.  
  
8.  In the **Launch Permission** dialog box, add or delete users, and assign the appropriate permissions to the appropriate users and groups. The available permissions are Local Launch, Remote Launch, Local Activation, and Remote Activation. The Launch rights grant or deny permission to start and stop the service; the Activation rights grant or deny permission to connect to the service.  
  
9. Click OK to close the dialog box.  
  
10. Under **Access Permissions**, repeat steps 7 and 8 to assign the appropriate permissions to the appropriate users and groups.  
  
11. Close the MMC snap\-in.  
  
12. Restart the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service.  
  
#### To configure rights for remote users on Windows 2000 with the latest service packs  
  
1.  Run **dcomcnfg.exe** at the command prompt.  
  
2.  On the **Applications** page of the **Distributed COM Configuration Properties** dialog box, select SQL Server Integration Services 11.0 and then click **Properties**.  
  
3.  Select the **Security** page.  
  
4.  Use the two separate dialog boxes to configure **Access Permissions** and **Launch Permissions**. You cannot distinguish between remote and local access \- Access permissions include local and remote access, and Launch permissions include local and remote launch.  
  
5.  Close the dialog boxes and **dcomcnfg.exe**.  
  
6.  Restart the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service.  
  
## Connecting by using a Local Account  
 If you are working in a local Windows account on a client computer, you can connect to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service on a remote computer only if a local account that has the same name and password and the appropriate rights exists on the remote computer.  
  
## Delegation Is Not Supported  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] does not support the delegation of credentials, sometimes referred to as a double hop. In this scenario, you are working on a client computer, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is installed on a second computer, and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed on a third computer. Although [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] successfully passes your credentials from the client computer to the second computer on which [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is running, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] cannot delegate your credentials from the second computer to the third computer on which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is running.  
  
## See Also  
 [Configure a Windows Firewall for Access to the SSIS Service](../../Topics\TopicNameContainA/Configure-a-Windows-Firewall-for-Access-to-the-SSIS-Service.md)  
  
  