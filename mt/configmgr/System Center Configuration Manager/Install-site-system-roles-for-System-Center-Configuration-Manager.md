---
title: "Install site system roles for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-04-25
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 61f5c774-7667-44ae-b8e4-a4951318b183
caps.latest.revision: 4
---
# Install site system roles for System Center Configuration Manager
The  [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console has two wizards you can use to install site system roles:  
  
-   **Add Site System Roles Wizard**: Use this wizard to add site system roles to an existing site system server in the site.  
  
-   **Create Site System Server Wizard**: Use this wizard to specify a new server as a site system server, and then install one or more site system roles on the server. This wizard is the same as the **Add Site System Roles Wizard**, except that on the first page, you must specify the name of the server to use and the site in which you want to install it.  
  
 When you install a site system role on a remote computer (including an instance of the SMS Provider), the computer account of the remote computer is added to a local group on the site server. When the site is installed on a domain controller, the group on the site server is a domain group instead of a local group, and the remote site system role is not operational until either the site system role computer restarts, or the Kerberos ticket for the remote computers [Accounts used in System Center Configuration Manager](../System Center Configuration Manager/Accounts-used-in-System-Center-Configuration-Manager.md) account is refreshed.  
  
 Just prior to installing the site system role, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] checks the destination computer to ensure it meets the prerequisites for the site system roles you have selected. When installing site system roles:  
  
-   By default, when [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs a site system role, the installation files are installed on the first available NTFS formatted disk drive that has the most available free disk space. To prevent [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] from installing on specific drives, create an empty file named **no_sms_on_drive.sms** and copy it to the root folder of the drive before you install the site system server.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses the **Site System Installation Account** to install site system roles. You specify this account when you run the applicable wizard to create a new site system server or add site system roles to an existing site system server. By default, this account is the local system account of the site server computer, but you can specify a domain user account for use as the Site System Installation Account. For more information see the Site System Installation Account in the [Accounts used in System Center Configuration Manager](../System Center Configuration Manager/Accounts-used-in-System-Center-Configuration-Manager.md) topic.  
  
##  <a name="bkmk_Install"></a> To install site system roles on an existing site system server  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, click **Servers and Site System Roles**, and then select the server that you want to use for the new site system roles.  
  
3.  On the **Home** tab, in the **Server** group, click **Add Site System Roles**.  
  
4.  On the **General** page, review the settings, and then click **Next**.  
  
    > [!TIP]  
    >  To access the site system role from the Internet, ensure that you specify an Internet FQDN.  
  
5.  On the **Proxy** page, specify settings for a proxy server if site system roles that run on this site system server require a proxy server to connect to locations on the Internet, and then click **Next**.  
  
6.  On the **System Role Selection** page, select the site system roles that you want to add, and then click **Next**.  
  
7.  Complete the wizard.  
  
> [!TIP]  
>  The Windows PowerShell cmdlet, New-CMSiteSystemServer, performs the same function as this procedure. For more information, see [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) in the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] SP1 Cmdlet Reference documentation.  
  
## To install site system roles on a new site system server  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, and click **Servers and Site System Roles**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Site System Server**.  
  
4.  On the **General** page, specify the general settings for the site system, and then click **Next**.  
  
    > [!TIP]  
    >  To access the new site system role from the Internet, ensure that you specify an Internet FQDN.  
  
5.  On the **Proxy** page, specify settings for a proxy server if site system roles that run on this site system server require a proxy server to connect to locations on the Internet, and then click **Next**.  
  
6.  On the **System Role Selection** page, select the site system roles that you want to add, and then click **Next**.  
  
7.  Complete the wizard.  
  
> [!TIP]  
>  The Windows PowerShell cmdlet, New-CMSiteSystemServer, performs the same function as this procedure. For more information, see [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) in the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] SP1 Cmdlet Reference documentation.  
  
## See Also  
 [Add site system roles for System Center Configuration Manager](../System Center Configuration Manager/Add-site-system-roles-for-System-Center-Configuration-Manager.md)