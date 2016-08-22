---
title: "Manage accounts to access content in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: a7df9d0f-fbde-47eb-97e7-3d29536424fa
caps.latest.revision: 4
---
# Manage accounts to access content in System Center Configuration Manager
Before deploying content in [!INCLUDE[cm6long_md](../System Center Configuration Manager/itokens/cm6long_md.md)], take time to consider how clients will access that content from distribution points.  
  
-   **Network Access Account** – Used by clients to connect to a distribution point and access content. By default, clients will first try their computer account  
  
     This account is also used by pull-distribution points to obtain content from a source distribution point in a remote forest  
  
-   **Package access account** – By default, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] grants access to content on a distribution point to generic access accounts Users and Administrators. However, you can configure additional permissions to restrict access.  
  
-   **Multicast Connection Account** – Used for operating system deployments.  
  
##  <a name="bkmk_NAA"></a> Network Access Account  
 Client computers use the Network Access Account when they cannot use their local computer account to access content on distribution points; for example, this applies to workgroup clients and computers from untrusted domains. This account might also be used during operating system deployment when the computer installing the operating system does not yet have a computer account on the domain.  
  
-   Clients only use the Network Access Account for accessing resources on the network  
  
-   You can configure multiple accounts for use as a Network Access Account at each primary site  
  
-   Clients first try access content on a distribution point using  use their *computername*$ account. IF this account fails, it then attempts to use a Network Access Account. Then, clients continue to attempt to use the Network Access Account even if it has previously failed.  
  
 **Permissions**: Grant this account the minimum appropriate permissions to access the software for the content that the client requires.  
  
-   The account must have the **Access this computer from the network** right on the distribution point.  
  
-   Create the account in any domain that provides the necessary access to resources. The Network Access Account must always include a domain name. Pass-through security is not supported for this account. If you have distribution points in multiple domains, create the account in a trusted domain.  
  
> [!TIP]  
>  To avoid account lockouts, do not change the password on an existing Network Access Account. Instead, create a new account and configure the new account in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. When sufficient time has passed for all clients to have received the new account details, remove the old account from the network shared folders and delete the account.  
  
> [!IMPORTANT]  
>  Do not grant this account interactive logon rights.  
>   
>  Do not grant this account the right to join computers to the domain. If you must join computers to the domain during a task sequence, use the Task Sequence Editor Domain Joining Account.  
  
### To configure the Network Access Account  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration** >   **Site Configuration** >  **Sites**, and then select the site.  
  
2.  On the **Settings** group, click **Configure Site Components** > **Software Distribution**.  
  
3.  Click the **Network Access Account** tab. Configure one or more accounts and then click **OK**.  
  
##  <a name="bkmk_Paa"></a> Package access accounts  
 Package Access Accounts enable you to set NTFS file system permissions to specify the users and user groups that can access package content on distribution points. By default, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] grants access only to the generic access accounts **Users** and **Administrators**, but you can control access for client computers by using additional Windows accounts or groups. Mobile devices always retrieve package content anonymously; therefore, mobile devices do not use the Package Access Accounts.  
  
 By default, when [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] copies the content files in a package to a distribution point, it grants **Read** access to the local **Users** group and **Full Control** to the local **Administrators** group. The actual permissions that are required depend on the package. If you have clients in workgroups or in untrusted forests, those clients use the Network Access Account to access the package content. Ensure that the Network Access Account has permissions to the package by using the defined Package Access Accounts.  
  
 Use accounts in a domain that can access the distribution points. If you create or modify the account after the package is created, you must redistribute the package. Updating the package does not change the NTFS file system permissions on the package.  
  
 You do not have to add the Network Access Account as a Package Access Account, because membership of the **Users** group adds it automatically. Restricting the Package Access Account to only the Network Access Account does not prevent clients from accessing the package.  
  
### To manage access accounts  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, select one of the following steps for the type of content for which you want to manage access accounts:  
  
    -   **Applications**: Expand **Application Management**, click **Applications**, and then select the applications for which to manage access accounts.  
  
    -   **Packages**: Expand **Application Management**, click **Packages**, and then select the packages for which to manage access accounts.  
  
    -   **Deployment Packages**: Expand **Software Updates**, click **Deployment Packages**, and then select the deployment packages for which to manage access accounts.  
  
    -   **Driver Packages**: Expand **Operating Systems**, click **Driver Packages**, and then select the driver packages for which to manage access accounts.  
  
    -   **Operating System Images**: Expand **Operating Systems**, click **Operating System Images**, and then select the operating system images for which to manage access accounts.  
  
    -   **Operating System Installers**: Expand **Operating Systems**, click **Operating System Installers**, and then select the operating system installers for which to manage access accounts.  
  
    -   **Boot Images**: Expand **Operating Systems**, click **Boot Images**, and then select the boot images for which to manage access accounts.  
  
3.  Right-click the selected object, and then click **Manage Access Accounts**.  
  
4.  In the **Add Account** dialog box, specify the account type that will be granted access to the content, and then specify the access rights associated with the account.  
  
    > [!NOTE]  
    >  When you add a user name for the account and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] finds a local user account and a domain user account with that name, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sets access rights for the domain user account.  
  
##  <a name="bkmk_multi"></a> Multicast Connection Account  
 The Multicast Connection Account is used by distribution points that are configured for multicast to read information from the site database.  
  
-   You specify an account to use when you configure [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database connections for multicast  
  
-   By default, the computer account of the distribution point is used, but you can configure a user account instead  
  
-   You must specify a user account whenever the site database is in an untrusted forest  
  
-   The account must have **Read** permissions to the site database  
  
 For example, if your data center has a perimeter network in a forest other than the site server and site database, you can use this account to read the multicast information from the site database.  
If you create this account, create it as a low-rights, local account on the computer that runs Microsoft SQL Server.  
  
> [!IMPORTANT]  
>  Do not grant this account interactive logon rights  

## See Also
[Fundamental concepts for content management](../System Center Configuration Manager/Fundamental-concepts-for-content-management-in-System-Center-Configuration-Manager.md)