---
title: Upgrade and Installation FAQ (SQL Server R Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
---
# Upgrade and Installation FAQ (SQL Server R Services)
  This topic provides answers to common questions about installation, and questions about upgrades from  preview releases of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].  
  
 If you are installing [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] for the first time,  follow the procedures for setting up [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and the R components  as described here: [Set up SQL Server R Services &#40;In-Database&#41;](../Topic/Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md).  

   
## Changes in setup  
 The process for setup of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] has become much simpler; you can install all related features, including the R  components, by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup Wizard. You can also install the R packages and tools on a data science workstation \(no [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] required\) to connect to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and deploy R solutions.  
  
> [!NOTE]  
>   If you installed an early pre-release version of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], we recommend that you upgrade as soon as possible.  
Installation of early preview versions is no longer supported.   

## Uninstalling previous versions

It is important that you uninstall previous versions of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] in the correct order.

### 1. Run script to deregister Windows user group and components before uninstalling previous components
If you installed a previous pre-release version of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], you must first run run the script `RegisteREext.exe` with the `/uninstall` argument.

By doing so, you deregister old components and remove the Windows user group associated with Launchpad. If you do not do this, you will be unable to create the Windows user group required for any new instances that you install.

  
For example, if you installed R Services on the default instance, run this command:  
  
~~~~
    RegisterRExt.exe /UNINSTALL  
~~~~ 
  
If you installed R Services  on a named instance, specify the instance name after *INSTANCE:*  
  
~~~~ 
RegisterRExt.exe /UNINSTALL /INSTANCE:<instancename>   
~~~~  

> [!NOTE]  
>  The default location for this script changed after CTP 3.3. If you try to run the old version of the script, you might get an error. For RC0, the location of the script file was `C:\Program Files\Microsoft\MRO-for-RRE\8.0\R-3.2.2\library\RevoScaleR\rxLibs\x64`  
>   
>  If you have CTP 3.1, 3.2, or 3.3, you might also need to download an updated version of the post\-installation configuration script from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=723194). The updated script supports de\-registration of older components.  
> Click the link and select **Save As** to save the script to a local folder. Rename the existing script, and then copy the new script into the folder where the script will be executed.  

### 2. Uninstall any older versions of the Revolution Enterprise tools, including components installed with CTP releases.

The order of uninstallation of the R comp-onents is also important. Always uninstall [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] first, and then uninstall [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)].  

 If you mistakenly uninstall R Open first and then get an error when trying to uninstall Revolution R Enterprise, one workaround is to reinstall Revolution R Open or Microsoft R Open, and then uninstall both components in the correct order.  

### 3. Uninstall any other version of Microsoft R Open.

Finally, uninstall all other versions of Microsoft R Open.
 
### 4. Upgrade SQL Server  
  
After all pre-release components have been uninstalled, restart the computer. This is a requirement of SQL Server setup and you will not be able to proceed with an updated installation until a restart is completed.     

After this is done, run SQL Server setup and follow these instructions to install [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]: [Set up SQL Server R Services](Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md).  
  
No additional components are needed; the R packages and connectivity packages are installed by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup. 

### Problems uninstalling older versions of R  
In some cases, older versions of Revolution R Open or Revolution R Enterprise are not completely removed by the uninstall process.  
  
 If you have problems removing an older version, you can also edit the registry to remove related keys.  
  
 Open the Windows Registry, and locate this key: `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.  
  
 Delete any of the following entries, if present, and if the key contains only a single value `sEstimatedSize2`:  
  
-   E0B2C29E\-B8FC\-490B\-A043\-2CAE75634972        \(for 8.0.2\)  
  
-   46695879\-954E\-4072\-9D32\-1CC84D4158F4        \(for 8.0.1\)  
  
-   2DF16DF8\-A2DB\-4EC6\-808B\-CB5A302DA91B        \(for 8.0.0\)  
  
-   5A2A1571\-B8CD\-4AAF\-9303\-8DF463DABE5A        \(for 7.5.0\)  


## New license agreement for R components required for unattended installs  
 If you use the command line to upgrade an instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that already has [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] installed, you must modify the command line to use the new license agreement parameter, *\/IACCEPTROPENLICENSEAGREEMENT*. 
 
 Failure to use the correct argument can cause [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup to fail.  
  
## After running setup, [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] is still not enabled  
 The feature that supports running external scripts is disabled by default, even if installed. This is by design, for surface area reduction.  
  
 To enable R scripts, an administrator can run the following statement in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]:  
  
1.  On the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance where you want to use R, run this statement.  
  
    ```  
    sp_configure 'external scripts enabled',1'  
    reconfigure with override  
    ```  
  
2.  Restart the instance.  
  
3.  After the instance has restarted, open **SQL Server Configuration Manager** or the **Services** panel and verify that the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service is running.  


## Setup of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] not available in a failover cluster  
 Currently, it is not possible to install [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] on a failover cluster.  
  
 However, you can install [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] on a standalone computer that uses Always On and is part of an availability group. For more information about using R Services in an Always On availability group, see [Always On Availability Groups: Interoperability](Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md).  

  
## Launchpad service cannot be started  
 To install R Services \(In\-Database\), the drive where the feature is installed must support creation of short file names using the **8dot3** notation.  \(An 8.3 filename is also called a short filename and is used for compatibility with older versions of Microsoft Windows prior or as an alternate filename to the long filename.\) If the volume where you are installing [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] does not support the short filenames, the processes that launch R from SQL Server might not be able to locate the correct executable and the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] will not start.  
  
 As a workaround, you should enable the 8dot3 notation on the volume and reinstall.  
  
 If that is not possible, edit the configuration file to use the long file name. For example, if the configuration file uses the short file path "\<drive\>:\\MSSQL13.SQLSERVER", edit the setting to use the full file path "\<drive\>:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER"  
  
## Side by side installation not supported  
 Do not create a side\-by\-side installation using another version of R or other releases from Revolution Analytics.  
  
## Unable to launch runtime for R script
[!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] creates a Windows users group that is used by the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] to run R jobs. This user group must have the ability to log into the instance that is running R Services in order to execute R on the behalf of remote users who are using Windows integrated authentication.
  
 In an environment where the Windows group for R users \(**SQLRUsers**\) does not have this permission, you might see the following errors:  
  
-   When trying to run R scripts:  
  
     *Unable to launch runtime for 'R' script. Please check the configuration of the 'R' runtime.*  
  
     *An external script error occurred. Unable to launch the runtime.*  
  
-   Errors generated by the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service:  
  
     *Failed to initialize the launcher RLauncher.dll*  
  
     *No launcher dlls were registered\!*  
  
-   Security logs indicate that the account, NT SERVICE\\MSSQLLAUNCHPAD was unable to log in.  
  
For information about how to give this user group the necessary permissions, see [Set up SQL Server R Services](Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md).../Topic/Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\.md). 

> [!NOTE]
> 
> This limitation does not apply if you use SQL logins to run R scripts from a remote workstation. 

  
## Remote execution via ODBC   
 If you use a data science workstation and connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer to run R commands using the **RevoScaleR** functions, you might get an error when using ODBC calls that write data to the server. 
 
 The reason is the same  as described in the previous section: namely, the default user group that was created by setup for running R tasks does not have write permissions on the server.  
  
For information about how to give this user group the necessary permissions, see [Set up SQL Server R Services](Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md). 
  
  
## Setting up [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] in an Azure Virtual Machine  
 If you install [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on an Azure virtual machine by using one of the images that includes [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], some additional steps are needed.  
  
-   **Install [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]**  
  
     R Services \(In\-Database\) is not installed by default with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. Therefore, after you have created the Azure virtual machine, you will need to re\-run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup, add the feature on the **Server Configuration** page of the wizard, and restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance.  
  
-   **Unblock firewall**  
  
     You will also need to make some additional changes to the firewall on the virtual machine to ensure that you can access the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance from a remote data science client.  
  
     For example, you might not be able to use compute contexts that require use of the virtual machine's workspace. The reason is that, by default, the firewall on the Azure virtual machine includes a rule that blocks network access for local R user accounts.  
  
     As a workaround, on the virtual machine, open Windows Firewall with Advanced Security, select **Outbound Rules**, and disable the following rule:  
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`  
  
-   **Install required network protocols**  
  
     Currently, [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] uses the Named Pipes protocol for connections between the client and server computers. If Named Pipes is not enabled, you must install and enable it on both the Azure virtual machine and any data science clients that connect tothe server.  
  
## Errors during setup because R components cannot be installed  
 When you install R Services \(In\-Database\) by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup, when you click **Accept** on the page containing the Microsoft R Open license terms, setup should locate the components and begin installation when other components are installed. However, in these cases, the components might fail to install:  
  
-   You are performing an offline install and the components cannot be downloaded.  
  
     [Installing R Components without Internet Access](../../Topics\TopicNameNotContainA/Installing-R-Components-without-Internet-Access.md)  
  
-   You are using the option to check for updates and the update service returns an error because it cannot find the correct version of the component.  
  
  This is a known issue that has been fixed in RC3.  
  
 
  
## Upgrade of R Server \(Standalone\) to RC3 requires uninstallation using the RC2 setup utility
 Microsoft R Server \(Standalone\) first became available in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC2. To upgrade to the RC3 version of Microsoft R Server, you must first uninstall using [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC2 setup, and then reinstall using [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC3 setup.  
  
1.  Uninstall R Server \(Standalone\) for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC2 using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup.  
  
2.  Upgrade [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] to RC3 and select the option to install R Services \(In\-Database\). This upgrades the instance of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] to RC3; no additional configuration is necessary.  
  
3.  Run [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] setup for RC3 once more, and install Microsoft R Server \(Standalone\).  

This workaround is not required when upgrading to the RTM version of Microsoft R Server.

## See Also  
 [Getting Started with SQL Server R Services](../../Topics\TopicNameNotContainA/Getting-Started-with-SQL-Server-R-Services.md)   
 [Getting Started with Microsoft R Server &#40;Standalone&#41;](../Topic/Getting%20Started%20with%20Microsoft%20R%20Server%20\(Standalone\).md)  
  
  