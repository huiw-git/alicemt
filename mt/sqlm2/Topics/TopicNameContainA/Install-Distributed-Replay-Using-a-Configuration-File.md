---
title: Install Distributed Replay Using a Configuration File
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3259232c-6963-4c9c-9d10-ae42aa262eef
robots: noindex,nofollow
---
# Install Distributed Replay Using a Configuration File
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup provides the ability to generate a configuration file based on user input and system defaults. If you specify that you want the Management tools installed, you can use the configuration file to deploy the three Distributed Replay components \(administration tool, Distributed Replay controller, and the Distributed Replay client\). It supports Installing, repairing, and uninstalling of the Distributed Replay components.  
  
 Setup supports the use of the configuration file only through the command\-line. The processing order of the parameters while using the configuration file is outlined below:  
  
-   The configuration file overwrites the defaults in a package  
  
-   Command\-line values overwrite the values in the configuration file  
  
 For more information about how to use a configuration file, see [Install SQL Server 2016 Using a Configuration File](../../Topics\TopicNameContainA/Install-SQL-Server-2016-Using-a-Configuration-File.md).  
  
> [!IMPORTANT]  
>  After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server. For more information, see [Complete the Post-Installation Steps](../../Topics\TopicNameNotContainA/Complete-the-Post-Installation-Steps.md).  
  
### To generate a configuration file  
  
1.  Follow the Setup wizard through to the **Ready to Install** page. The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.  
  
2.  Cancel the setup without actually completing the installation, to generate the INI file.  
  
### To Install Distributed Replay Using the Configuration File  
  
-   Run the installation through the command prompt and supply the ConfigurationFile.ini using the ConfigurationFile parameter.  
  
 **Sample Syntax**  
  
 Following is an example on how to specify the configuration file at the command prompt:  
  
```  
Setup.exe /CTLRSVCPASSWORD="ctlrsvcpswd" /CLTSVCPASSWORD="cltsvcpswd" / ConfigurationFile=ConfigurationFile.INI\  
```  
  
> [!NOTE]  
>  You must specify both passwords in the command line because you cannot configure them in the configuration file.  
  
  