---
title: "How to upgrade clients on Mac computers in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 74c60941-5eae-4905-9e58-252bdb39df96
caps.latest.revision: 10
---
# How to upgrade clients on Mac computers in System Center Configuration Manager
Follow the high-level steps described below  to upgrade the client for Mac computers by using a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] application. Alternatively, you can also download the Mac client installation file, copy it to a shared network location or a local folder on the Mac computer and then instruct users to run the installation manually.  
  
> [!NOTE]  
>  Before you perform these steps, make sure that your Mac computer meets the prerequisites listed in the [On-premises mobile device management](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md#bkmk_OnpremOS) section in [Supported operating systems for sites and clients for System Center Configuration Manager](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md).  
  
## Step 1: Download the latest Mac client installation file from the Microsoft Download Center  
 The Mac client for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is not supplied on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installation media and must be downloaded from the Microsoft Download Center. The Mac client installation files are contained in a Windows Installer file named ConfigmgrMacClient.msi.  
  
 You can download this file from the [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=525184).  
  
## Step 2: Run the downloaded installation file to create the Mac client installation file  
 On a computer that runs Windows, run the **ConfigmgrMacClient.msi** that you downloaded to unpack the Mac client installation file, named **Macclient.dmg**. This file can be found, by default, in the **C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client** folder on the Windows computer after you have unpacked the files.  
  
## Step 3: Extract the client installation files  
 Copy the Macclient.dmg file to a network share, or a local folder on a Mac computer. Then, from the Mac computer, mount and then open the Macclient.dmg file and copy the files to a folder on the Mac computer.  
  
## Step 4: Create a .cmmac file that can be used to create an application  
  
1.  Use the **CMAppUtil** tool (found in the **Tools** folder of the Mac client installation files) to create a .cmmac file from the client installation package. This file will be used to create the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] application.  
  
2.  Copy the new file **CMClient.pkg.cmmac** file to a location that is available to the computer that is running the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
 For more information, see the [Step 1: Prepare Mac applications for Configuration Manager](../System Center Configuration Manager/Creating-Mac-computer-applications-with-System-Center-Configuration-Manager.md#BKMK_Step1) section in [Creating Mac computer applications with System Center Configuration Manager](../System Center Configuration Manager/Creating-Mac-computer-applications-with-System-Center-Configuration-Manager.md).  
  
## **Step 5:** Create and deploy an application containing the Mac client files  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, create an application from the **CMClient.pkg.cmmac** file that contains the client installation files.  
  
2.  Deploy this application to Mac computers in your hierarchy.  
  
 For more information, see  [Creating Mac computer applications with System Center Configuration Manager](../System Center Configuration Manager/Creating-Mac-computer-applications-with-System-Center-Configuration-Manager.md).  
  
## Step 6: Users install the latest client  
 Users of Mac clients will be prompted that an update to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is available and must be installed. After users install the client, they must restart their Mac computer.  
  
 After the computer restarts, the Computer Enrollment wizard automatically runs to request a new user certificate.  
  
 If you do not use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] enrollment but install the client certificate independently from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Configure the upgraded client to use an existing certificate](#BKMK_UpgradingClient_MachineEnrollment).  
  
##  <a name="BKMK_UpgradingClient_MachineEnrollment"></a> Configure the upgraded client to use an existing certificate  
 Run the following procedure to prevent the Computer Enrollment Wizard from running and to configure the upgraded client to use an existing client certificate.  
  
-   In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, create a configuration item of the type **Mac OS X**.  
  
-   Add a setting to this configuration item with the setting type **Script**.  
  
-   Add the following script to the setting:  
  
    ```  
    #!/bin/sh  
    echo "Starting script\n"  
    echo "Changing directory to MAC Client\n"  
    cd /Users/Administrator/Desktop/'MAC Client'/  
    echo "Import root cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/Root.pfx -A -k /Library/Keychains/System.Keychain -P ROOT  
    echo "Using openssl to convert pfx to a crt\n"  
    /usr/bin/sudo openssl pkcs12 -in /Users/Administrator/Desktop/'MAC Client'/Root.pfx -out Root1.crt -nokeys -clcerts -passin pass:ROOT  
    echo "Adding trust to root cert\n"  
    /usr/bin/sudo /usr/bin/security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.Keychain Root1.crt  
    echo "Import client cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/MacClient.pfx -A -k /Library/Keychains/System.Keychain -P MAC  
    echo "Executing ccmclient with MP\n"  
    sudo ./ccmsetup -MP https://SCCM34387.SCCM34387DOM.NET/omadm/cimhandler.ashx  
    echo "Editing Plist file\n"  
    sudo /usr/libexec/Plistbuddy -c 'Add:SubjectName string CMMAC003L' /Library/'Application Support'/Microsoft/CCM/ccmclient.plist  
    echo "Changing directory to CCM\n"  
    cd /Library/'Application Support'/Microsoft/CCM/  
    echo "Making connection to the server\n"  
    sudo open ./CCMClient  
    echo "Ending Script\n"  
    exit  
  
    ```  
  
-   Add the configuration item to a configuration baseline, and then deploy the configuration baseline to all Mac computers that install a certificate independently from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 For more information about how to create and deploy configuration items for Mac computers, see [How to create configuration items for Mac OS X devices managed with the System Center Configuration Manager client](../System Center Configuration Manager/How-to-create-configuration-items-for-Mac-OS-X-devices-managed-with-the-System-Center-Configuration-Manager-client.md) and [How to deploy configuration baselines in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-configuration-baselines-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Upgrade clients in System Center Configuration Manager](../System Center Configuration Manager/Upgrade-clients-in-System-Center-Configuration-Manager.md)