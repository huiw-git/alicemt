---
title: View and Read SQL Server Setup Log Files
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
---
# View and Read SQL Server Setup Log Files
  Each execution of Setup creates log files are created with a new timestamped log folder at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\. The time\-stamped log folder name format is YYYYMMDD\_hhmmss. When Setup is run in an unattended mode, the logs are created at % temp%\\sqlsetup\*.log. All files in the logs folder are archived into the Log\*.cab file in their respective log folder.  
  
 A typical Setup request goes through three execution phases:  
  
1.  Global rules text  
  
2.  Component update  
  
3.  User\-requested action  
  
 In each phase, Setup generates detail and summary logs with additional logs created as appropriate. Setup is called at least three times per user\-requested Setup action.  
  
 Datastore files contain a snapshot of the state of all configuration objects being tracked by the Setup process, and are useful for troubleshooting configuration errors. XML file dumps are created for datastore objects for each execution phase. They are saved in their own log subfolder under the time\-stamped log folder, as follows:  
  
-   Datastore\_GlobalRules  
  
-   Datastore\_ComponentUpdated  
  
-   Datastore  
  
 The following sections describe [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup log files.  
  
## Summary Text  
  
### Overview  
 This file shows the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components that were detected during Setup, the operating system environment, command\-line parameter values if they are specified, and the overall status of each MSI\/MSP that was executed.  
  
 The log is organized into the following sections:  
  
-   An overall summary of the execution  
  
-   Properties and the configuration of the computer where [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup was run  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] product features previously installed on the computer  
  
-   Description of the installation version and installation package properties  
  
-   Runtime input settings that are provided during install  
  
-   Location of the configuration file  
  
-   Details of the execution results  
  
-   Global rules  
  
-   Rules specific to the installation scenario  
  
-   Failed rules  
  
-   Location of the rules report file  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\.  
  
 To find errors in the summary text file, search the file by using the "error" or "failed" keywords.  
  
## Summary\_engine\-base\_YYYYMMDD\_HHMMss.txt  
  
### Overview  
 The summary\_engine base file is similar to the summary file and is generated during the main workflow.  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## Summary\_engine\-base\_YYYYMMDD\_HHMMss\_ComponentUpdate.txt  
  
### Overview  
 The component update summary log file is similar to the summary file and is generated during the component update workflow.  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## Summary\_engine\-base\_\<VersionNumber\>MMDD\_HHMMss\_GlobalRules.txt  
  
### Overview  
 The global rules summary log file is similar to the summary file generated during the global rules workflow.  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## Detail.txt  
  
### Overview  
 Detail.txt is generated for the main workflow such as install or upgrade, and provides the details of the execution. The logs in the file are generated based on the time when each action for the installation was invoked, and show the order in which the actions were executed, and their dependencies.  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup  
  
 Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\Detail.txt.  
  
 If an error occurs during the Setup process, the exception or error are logged at the end of this file. To find the errors in this file, first examine the end of the file followed by a search of the file for the "error" or "exception" keywords.  
  
## Detail\_ComponentUpdate.txt  
  
### Overview  
 The Detail\_ComponentUpdate.txt file is generated for the component update workflow and is similar to Detail.txt.  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## Detail\_GlobalRules.txt  
  
### Overview  
 Detail\_GlobalRules.txt is generated for the global rules execution and is similar to Detail.txt.  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## MSI log files  
  
### Overview  
 The MSI log files provide details of the installation package process. They are generated by the MSIEXEC during the installation of the specified package.  
  
 Types of MSI log files:  
  
-   \<Feature\>\_\<Architecture\>\_\<Interation\>.log  
  
-   \<Feature\>\_\<Architecture\>\_\<Language\>\_\<Interation\>.log  
  
-   \<Feature\>\_\<Architecture\>\_\<Interation\>\_\<workflow\>.log  
  
### Location  
 The MSI log files are located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\\<Name\>.log.  
  
 At the end of the file is a summary of the execution which includes the success or failure status and properties. To find the error in the MSI file, search for "value 3" and usually the errors can be found close to the string.  
  
## ConfigurationFile.ini  
  
### Overview  
 The configuration file contains the input settings that are provided during installation. It can be used to restart the installation without having to enter the settings manually. However, passwords for the accounts, PID, and some parameters are not saved in the configuration file. The settings can be either added to the file or provided by using the command line or the Setup user interface. For more information, see [Install SQL Server 2016 Using a Configuration File](../../Topics\TopicNameContainA/Install-SQL-Server-2016-Using-a-Configuration-File.md).  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## SystemConfigurationCheck\_Report.htm  
  
### Overview  
 The system configuration check report contains a short description for each executed rule, and the execution status.  
  
### Location  
 It is located at %programfiles%\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\130\\Setup Bootstrap\\Log\\\<YYYYMMDD\_HHMM\>\\.  
  
## See Also  
 [Install SQL Server 2016](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016.md)  
  
  