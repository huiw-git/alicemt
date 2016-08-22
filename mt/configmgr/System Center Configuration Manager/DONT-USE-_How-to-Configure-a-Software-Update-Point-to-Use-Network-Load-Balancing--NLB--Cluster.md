---
title: "DONT USE _How to Configure a Software Update Point to Use Network Load Balancing (NLB) Cluster"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5685fa28-b50f-4f0d-8858-91111cb9a437
caps.latest.revision: 4
caps.handback.revision: 0
---
# DONT USE _How to Configure a Software Update Point to Use Network Load Balancing (NLB) Cluster
> [!NOTE]  
>  The information in this topic applies only to [!INCLUDE[cm5long](../System Center Configuration Manager/itokens/cm5long_md.md)] with no service pack. For more information about whether to configure a software update point to use Network Load Balancing (NLB) in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see the [Software Update Point Configured to Use an NLB](assetId:///bcf8ed65-3bea-4bec-8bc5-22d9e54f5a6d#BKMK_NLBSUPSP1) section in the [Planning for Software Updates in Configuration Manager](assetId:///bcf8ed65-3bea-4bec-8bc5-22d9e54f5a6d) topic.  
  
 This topic provides the steps for how to configure NLB in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with no service pack. NLB can increase the reliability and performance of a network. You can set up multiple WSUS servers that share a single SQL Server failover cluster, and then configure a software update point to use the NLB, but this configuration requires that you perform additional steps during WSUS setup.  
  
> [!NOTE]  
>  The maximum number of WSUS servers that can be configured as part of a network load balancing cluster is four.  
  
 Use the following sections to configure an active software update point to use an NLB cluster:  
  
-   Prepare the network environment for network load balanced software update point site systems.  
  
-   Install WSUS 3.0 (on each server that will host the software update point site system role).  
  
-   Install the software update point site system role (on each server that will be part of the software update point network load balancing cluster).  
  
-   Configure the Windows Server network load balancing cluster for installed software update site systems.  
  
-   Configure the active software update point component for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site as the software update point network load balancing cluster.  
  
 [Configure WSUS for Network Load Balancing](http://go.microsoft.com/fwlink/p/?LinkId=232412)  
  
##  <a name="BKMK_PrepareNetworkForNLB"></a> Prepare the Network Environment for NLB Software Update Point Site Systems  
 Use the following procedure to prepare the network environment for the software update point to use an NLB cluster.  
  
###  <a name="BKMK_PrepareNetwork"></a> To prepare the network environment for NLB software update point site systems  
  
1.  Create or identify a domain user account to be used as the Software Update Point Connection account.  
  
2.  Add the computer accounts of each site system that will be configured as part of the software update point NLB cluster to the local Administrators group on each server that will be part of the NLB cluster.  
  
    > [!NOTE]  
    >  The computer accounts for the cluster nodes must be able to write to the WSUS database. If the local Administrators group is removed from the SysAdmin role on the SQL server, the computer accounts will not be able to write to the WSUS database, and the software update point will fail to install until the computer accounts are added to the SysAdmin role.  
  
3.  Create a DFS share or a standard network shared folder that is available to all of the WSUS servers that will be part of the software update point NLB cluster to be used as the WSUS resource content share. Each of the remote WSUS servers should be given change permissions on the root of the shared folder (all standard NTFS permissions except for Full Control). If the share is created on one of the site systems that will be part of the NLB cluster, the Network Access Account for the site system must have change permissions on the root of the shared folder. The user account used to run WSUS Setup must also have the same permissions to the share.  
  
4.  Identify the computer running SQL Server to host the WSUS database. The WSUS database can be installed on the same SQL Server database server instance that hosts the site database or a different SQL Server database server.  
  
    > [!NOTE]  
    >  For a list of supported SQL Server versions that you can use for site systems in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [SQL Server Site Database Configurations](assetId:///c1e93ef9-761f-4f60-8372-df9bf5009be0#BKMK_SupConfigSQLDBconfig).  
  
5.  The WSUS 3.0 Administration console must be installed on the primary site server to allow the site server and remote [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles to configure and synchronize with WSUS.  
  
6.  If the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site is configured to communicate by using SSL authentication, Web server signing certificates must be configured on each of the software update point site systems that will be configured as part of the NLB. For more information about configuring Web server signing certificates for network load balanced software update points, see [PKI Certificate Requirements for Configuration Manager](assetId:///19dedcfb-fb97-4c43-b777-e2701e935be7).  
  
##  <a name="BKMK_InstallWSUS"></a> Install WSUS 3.0 (on each server that will host the software update point site system role)  
  
> [!NOTE]  
>  The following procedure must be performed on each server that will be part of the software update point NLB cluster.  
  
#### To install WSUS 3.0 to support the Configuration Manager software update point site system role  
  
1.  On a server that will be part of the software update point NLB cluster, create the following folder: *<Program Files directory\>***\Update Services**.  
  
2.  Install WSUS 3.0 on each server that will be a member of the software update point NLB cluster. For more information about installing WSUS, see [Install the WSUS 3.0 SP2 Server Software Though the User Interface](http://go.microsoft.com/fwlink/p/?LinkID=232835) in the Windows Server Update Services documentation library. During installation, consider the following settings:  
  
    -   On the **Select Update Source** page, select the **Store updates locally** check box and enter the path *<Program Files directory\>***\Update Services**.  
  
    -   On the **Database Options** page, do one of the following.  
  
        -   If you are running WSUS Setup on the server hosting the WSUS SQL Server database, select **Use an existing database server on this computer** select the instance name to be used from the drop-down list.  
  
        -   If you are running WSUS Setup on a computer that will not host the WSUS SQL Server database, select **Use an existing database server on a remote computer** and enter the FQDN of the SQL Server that will host the WSUS database followed by the instance name (if not using the default instance).  
  
        > [!WARNING]  
        >  If another WSUS Server that will be part of the NLB cluster has been configured to use the same SQL Server database server, select **Use existing database**.  
  
3.  Add the Software Update Point Connection Account to the local **WSUS Administrators** group on the server.  
  
4.  On the SQL Server computer that hosts the WSUS database, provide dbo_owner rights on the **SUSDB** database for the Software Update Point Connection Account.  
  
5.  Configure Internet Information Services (IIS) to enable content share access.  
  
    1.  Open the Internet Information Services (IIS) Manager console.  
  
    2.  Expand *<server name\>*, expand **Sites**, and then expand the Site node for the WSUS Web site (either **Default Web Site** or **WSUS Administration**).  
  
    3.  Configure the virtual directory Content to use the UNC share name of the share created in step 3 of the [To prepare the network environment for network load balanced software update point site systems](assetId:///07683847-1b69-40d2-9dbd-74dec415bef8#BKMK_PrepareNetwork) procedure in this topic.  
  
    4.  Configure the credentials used to connect to the virtual directory with the user name and password of the Software Update Point Connection Account created in step 1 of the [To prepare the network environment for network load balanced software update point site systems](assetId:///07683847-1b69-40d2-9dbd-74dec415bef8#BKMK_PrepareNetwork) procedure in this topic.  
  
6.  Configure SSL authentication in Internet Information Services (IIS).  
  
    > [!IMPORTANT]  
    >  This step is only required if the software update point will be configured to communicate by using SSL. If you are not configuring the software update point to use SSL, skip to step 6.  
  
    1.  Open Internet Information Services (IIS) Manager.  
  
    2.  Expand **Web Sites**, and then expand the WSUS administration Web site (either **Default Web Site** or **WSUS Administration**).  
  
    3.  Configure the following virtual directories of the WSUS administration Web site to use SSL:**APIRemoting30**, **ClientWebService**, **DSSAuthWebService**, **ServerSyncWebService**, and **SimpleAuthWebService**.  
  
    4.  Close Internet Information Services (IIS) Manager.  
  
    5.  Run the following command from <*WSUS Installation Folder*>\Tools: **WSUSUtil.exe configuressl <***Intranet FQDN of the software update point site system node***>**.  
  
7.  Move the local content directory to the WSUS resource content share created in step 3 of the [To prepare the network environment for network load balanced software update point site systems](assetId:///07683847-1b69-40d2-9dbd-74dec415bef8#BKMK_PrepareNetwork) procedure in this topic.  
  
    > [!IMPORTANT]  
    >  This step must be followed for each of the front-end WSUS servers that are not on the same server as the WSUS resource content share  
  
    1.  Open a command window and navigate to the WSUS tools directory on the WSUS server: **cd Program Files\Update Services\Tools**  
  
    2.  On the first WSUS server to be configured, at the command prompt, type the following command:  
  
         **wsusutil movecontent** *<WSUSContentsharename\>* *<logfilename\>*  
  
         Where *<WSUSContentsharename\>* is the name of the WSUS content resource location share to which the content should be moved, and *logfilename* is the name of the log file that will be used to record the content move procedure.  
  
    3.  On the successive WSUS servers to be configured, at the command prompt type the following command:  
  
         **wsusutil movecontent** *<WSUSContentsharename\>* *<logfilename\>* **/skipcopy**  
  
         Where *<WSUSContentsharename\>* is the name of the WSUS content resource location share to which the content should be moved, and *logfilename* is the name of the log file that will be used to record the content move procedure.  
  
        > [!NOTE]  
        >  To verify that the content move was successful, review the log file created during the procedure and use registry editor to review the **HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup&#124;ContentDir** registry key to ensure that the value has been changed to the WSUS content resource location share name.  
  
## Install the Software Update Point Site System Role  
 Use the following procedure on each software update point that will be part of the software update point NLB cluster.  
  
#### To install the software update point site system role on servers that will be part of the network load balancing cluster  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration** and click **Servers and Site System Roles**.  
  
3.  Add the software update point site system role to a new or existing site system server by using the associated step:  
  
    > [!NOTE]  
    >  For more information about installing site system roles, see [Install and Configure Site System Roles for Configuration Manager](assetId:///5c669a3c-404f-4a5d-88f0-bc40443ebaae).  
  
    -   **New site system server**: On the **Home** tab, in the **Create** group, click **Create Site System Server**. The Create Site System Server Wizard opens.  
  
    -   **Existing site system server**: Click the server in which you want to install the software update point site system role. When you click a server, a list of the site system roles that are already installed on the server are displayed in the details pane.  
  
         On the **Home** tab, in the **Server** group, click **Add Site System Role**. The Add Site System Roles Wizard opens.  
  
4.  On the General page, specify the general settings for the site system server. When you add the software update point to an existing site system server, verify the values that were previously configured.  
  
5.  On the System Role Selection page, select **Software update point** from the list of available roles, and then click **Next**.  
  
6.  On the Software Update Point page, specify whether the site server will use a proxy server when software updates are synchronized and when downloading software update files, and whether to use credentials to connect to the proxy server. Click **Next**.  
  
7.  On the Active Settings page, click **Next**, and then click **Close** to exit the wizard and create the non-active software update point.  
  
## Configure the Windows Server Network Load Balancing Cluster for Installed Software Update Point Site Systems  
  
#### To configure the Windows Server network load balancing cluster for installed software update point site systems  
  
1.  To configure the Windows Server NLB cluster for installed software update point site systems, follow the instructions for deploying NLB for the operating system running on the site system. For Windows Server 2008 and Windows Server 2008 R2, see the [Network Load Balancing Deployment Guide](http://go.microsoft.com/fwlink/p/?LinkId=232840).  
  
2.  After you verify that the NLB cluster is operating successfully, you can configure the active software update point to use the NLB cluster.  
  
## Configure the Active Software Update Point to Use an NLB Cluster  
 Use the following procedure to configure the active software update point for the site to use an NLB cluster.  
  
#### To configure the active software update point to use an NLB cluster  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the Administration workspace, expand **Site Configuration** and click **Servers and Site System Roles**.  
  
3.  On the **Home** tab, click **Configure Site Components**, and then click **Software Update Point**. The Software Update Point Component Properties opens.  
  
4.  On the General tab, select **Use Network Load Balancing cluster for active software update point**.  
  
5.  
  
6.  Click **Settings** and configure the following NLB settings:  
  
    1.  **NLB address type**: Select **FQDN**.  
  
    2.  **Intranet FQDN or IP address**: Enter the FQDN that you created in step 6 of [Prepare the network environment for network load balanced software update point site systems](assetId:///07683847-1b69-40d2-9dbd-74dec415bef8#BKMK_PrepareNetworkForNLB).  
  
     Click **OK**.  
  
7.  Click **Set**, and then select to configure the Software Update Point Connection Account to use the Windows user account that you created in step 1 of the [To prepare the network environment for network load balanced software update point site systems](assetId:///07683847-1b69-40d2-9dbd-74dec415bef8#BKMK_PrepareNetwork) procedure in this topic.  
  
     Select **Existing account** to specify a Windows user account that has previously been configured as a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] account or select **New account** to specify a Windows user account that is not currently configured as a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] account. The user is displayed in the **Accounts** subfolder of the **Security** node in the **Administration** workspace with the Software Update Point Connection Account name. Click **OK**  
  
8.  Determine the communication settings that you want to use for the active software update point, and then click **OK**.  
  
## See Also  
 [Configuring Software Updates in Configuration Manager](assetId:///912bfec1-fd19-4f56-a840-4ecd643c541b)