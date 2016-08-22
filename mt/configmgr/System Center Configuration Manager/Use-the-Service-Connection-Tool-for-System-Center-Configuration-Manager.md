---
title: "Use the Service Connection Tool for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 6e4964c5-43cb-4372-9a89-b62ae6a4775c
caps.latest.revision: 11
---
# Use the Service Connection Tool for System Center Configuration Manager
Use the **service connection tool** when your Configuration Manager  site system servers are not connected to the Internet but you still would like to keep yourself up-to-date with the latest updates to Configuration Manager.  
  
 The tool enables you to connect to the Configuration Manager cloud service to manually upload usage information for your hierarchy, and to download updates. Uploading usage data is necessary to enable the cloud service to provide the correct updates for your deployment.  
  
 **Prerequisites for using the service connection tool:**  
  
-   You  have a service connection point installed, and it is set to **Offline, on-demand connection**.  
  
-   The tool must be run from a command prompt.  
  
-   Each computer where the tool runs (the service connection point computer, and the computer that is connected to the internet) must be a x64 bit system and  have the following installed:  
  
    -   Both the **Visual C++ Redistributable** x86 and x64 files.   By default, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs the x64 version on the computer that hosts the service connection point.  
  
         To download a copy of the Visual C++ files, visit [Visual C++ Redistributable Packages for Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=40784) at the Microsoft Download Center.  
  
    -   .NET Framework 4.5.2 or later.  
  
-   The account you use to run the tool must have:
    -   **Local administrator** permissions on the computer that hosts the service connection point (where the tool is run).
    -   **Read** permissions to the site database.  
        
     
  
-   You will need a USB drive with sufficient free space to store the files and updates, or another method to transfer files between the service connection point computer, and the computer that has access to the Internet. (This scenario assumes that your site and managed computers do not have a direct connection to the Internet.)  
  
 **There are three primary steps to using the service connection tool:**  
  
1.  **Prepare**:  This step puts your usage data into a .cab file and stores it on a USB drive (or alternate transfer location you specify).  
  
2.  **Connect**: This step has you run the tool on a remote computer that connects to the Internet to upload data and download updates.  
  
3.  **Import**: This step imports updates for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to your site so you can then view and install updates from the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)].  

Beginning with version 1606, when connecting to Microsoft you can upload multiple .cab files at one time (each from a different hierarchy), and specify a proxy server and a user for the proxy server.   

**To upload multiple .cab files:**
 -  Place each .cab file you export from separate hierarchies into the same folder. The name of each file must be unique, and you can manually rename them if necessary.
 -  Then, when you run the command to upload data to Microsoft, you specify the folder that contains the .cab files. (Prior to update 1606, you could only upload data from a single hierarchy at a time, and the tool required you to specify the name of the .cab file in the folder.)
 -  Later, when you run the import task on the service connection point of a hierarchy, the tool automatically imports only the data for that hierarchy.  
 
 **To specify a proxy server:**  
 You can use the following optional parameters to specify a proxy server (More information about using these parameters is available in the Command line parameters section of this topic):
  - **-proxyserveruri [FQDN_of_proxy_sever]**  Use this parameter to specify the proxy server to use for this connection. 
  -  **-proxyusername [username]**  Use this parameter when  you must specify a user for the proxy server.


  
## Use the service connection tool  
 You can find the service connection tool (**serviceconnectiontool.exe**), in the Configuration Manager installation media in **%path%/smssetup/tools/ServiceConnectionTool** folder.  
  
 In this procedure, the command-line examples use the following file names and folder locations (you do not need to use these paths and file names and instead can use alternatives that match your environment and preferences):  
  
-   The path to a USB Stick where data is stored for transfer between servers:  **D:\USB\\**  
  
-   The name of the .cab file that contains data exported from your site: **UsageData.cab**  
  
-   The name of the empty folder where downloaded updates for Configuration Manager will be stored for transfer between servers: **UpdatePacks**  
  
 On the computer that hosts the service connection point:  
  
-   Open a command prompt  with administrative privileges, and then change directories to the location that contains **serviceconnectiontool.exe**.  
  
     By default, you can  find this tool in the Configuration Manager installation media in **%path%\smssetup/tools\ServiceConnectionTool** folder. All of the files in this folder must be in the same folder for the service connection tool to work.  
  
 When you run the following command, the tool prepares a .cab file that contains usage information and to copies it  to a location you specify. The data in the .cab file is based on the level of diagnostic usage data your site is configured to collect. (see [Diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/Diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)).  Run the following command to create the .cab file:  
  
-   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  
  
 You will also need to copy the ServiceConnectionTool folder with all of its contents to the USB drive, or otherwise make it available on the computer you will use for steps 3 and 4.  
  
#### To use the service connection tool  
  
1.  On the computer that hosts the service connection point:  
  
    -   Open a command prompt  with administrative privileges, and then change directories to the location that contains **serviceconnectiontool.exe**.  
  
   
2.  Run the following command to have the tool prepare a .cab file that contains usage information and to copy it  to a location you specify:  
  
    -   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  
  
      If you will upload .cab files from more than one hierarchy at the same time, each .cab file in the folder must have a unique name. You can manually rename files that you add to the folder.
      
      If you want to  view the usage information that is gathered to be uploaded to the Configuration Manager cloud service, run the following command to export the same data as a .csv file which you can then view using an application like Excel:  
  
    -   **serviceconnectiontool.exe -export -dest D:\USB\UsageData.csv**  
  
3.  After the prepare step is complete, move the USB drive (or transfer the exported data by another method) to a computer that has access to the Internet.  
  
4.  On the computer with Internet access, open a command prompt  with administrative privileges, and then change directories to the location that contains a copy of the tool  **serviceconnectiontool.exe** and the additional files from that folder.  
  
5.  Run the following command to begin the upload of usage information and the download of updates for Configuration Manager:  
  
    -   **serviceconnectiontool.exe -connect -usagedatasrc D:\USB\UsageData.cab -updatepackdest D:\USB\UpdatePacks**  
    
    For more examples of this command line, see the [Command line options](../System Center Configuration Manager/Use-the-Service-Connection-Tool-for-System-Center-Configuration-Manager.md#bkmk_cmd) section later in this topic. 
  
    > [!NOTE]  
    >  When you run the command line to connect to the Configuration Manager cloud service, an error similar to the following might occur:  
    >   
    >  -   Unhandled Exception: System.UnauthorizedAccessException:  
    >   
    >      Access to the path 'C:\  
    >     Users\br\AppData\Local\Temp\extractmanifestcab\95F8A562.sql' is denied.  
    >   
    >  This error can be safely ignored and you can close the error window, and continue.  
  
6.  After the download of updates for Configuration Manager  is complete, move the USB drive (or transfer the exported data by another method) to the computer that hosts the service connection point.  
  
7.  On the computer that hosts the service connection point, open a command prompt  with administrative privileges, change directories to the location that contains **serviceconnectiontool.exe**, and then run the following command:  
  
    -   **serviceconnectiontool.exe -import -updatepacksrc D:\USB\UpdatePacks**  
  
8.  After the import completes, you can close the command prompt. (Only updates for the applicable hierarchy are imported).  
  
9. Open  the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and navigate to **Administration** >**Cloud Services** > **Updates and Servicing**. Updates that were imported are now available to install. For information about installing updates, see  [Install in-console updates for System Center Configuration Manager](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md).  
  
## <a name="bkmk_cmd"></a> Command line options  
 To view help information for the service connection point tool, open command prompt to the folder that contains the tool and run the command:  **serviceconnectiontool.exe**.  
  
|Command-line options|Details|  
|---------------------------|-------------|  
|**-prepare -usagedatadest [drive:][path][filename.cab]**|This command stores current usage data in a .cab file.<br /><br /> Run this command as a **local administrator** on the server that hosts the service connection point.<br /><br /> Example:   **-prepare -usagedatadest D:\USB\Usagedata.cab**|    
|**-connect -usagedatasrc [drive:][path] -updatepackdest [drive:][path] -proxyserveruri [FQDN of proxy server] -proxyusername [username]** <br /> <br /> If you use a version of Configuration Manager prior to 1606, you must specify the name of the .cab file, and cannot use the options for a proxy server.  The supported command parameters are: <br /> **-connect -usagedatasrc [drive:][path][filename] -updatepackdest [drive:][path]** |This command connects to the Configuration Manager cloud service to Upload the usage data .cab files from the specified location, and to download available update packs and console content. The options for proxy servers are optional.<br /><br /> Run this command as a **local administrator** on a computer that can connect to the Internet.<br /><br /> Example for connecting without a proxy server: **-connect -usagedatasrc D:\USB\ -updatepackdest D:\USB\UpdatePacks** <br /><br /> Example for connecting when you use a proxy server: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks -proxyserveruri itgproxy.redmond.corp.microsoft.com -proxyusername Meg** <br /><br /> If you use a version prior to 1606, you must specify a file name for the .cab file, and you cannot specify a proxy server. Use the following example command line: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks**|      
|**-import -updatepacksrc [drive:][path]**|This command imports the update packs and console content you previously downloaded into your Configuration Manager console.<br /><br /> Run this command as a **local administrator** on the server that hosts the service connection point.<br /><br /> Example:  **-import -updatepacksrc D:\USB\UpdatePacks**|  
|**-export -dest [drive:][path][filename.csv]**|This command exports usage data to a .csv file, which you can then view.<br /><br /> Run this command as a **local administrator** on the server that hosts the service connection point.<br /><br /> Example: **-export -dest D:\USB\usagedata.csv**|  
  
## See Also  
 [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md)
 
 
 
 
 
 
 