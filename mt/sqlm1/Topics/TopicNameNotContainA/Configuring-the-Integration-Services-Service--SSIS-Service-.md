---
title: Configuring the Integration Services Service (SSIS Service)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
---
# Configuring the Integration Services Service (SSIS Service)
    
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. Starting in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], you can manage objects such as packages on the Integration Services server.  
  
 The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service relies on a configuration file for its settings. By default, the name for this configuration file is MsDtsSrvr.ini.xml, and the file is located in the folder, %ProgramFiles%\\Microsoft SQL Server\\110\\DTS\\Binn.  
  
 Typically, you do not have to make any changes to this configuration file, nor do you have to change the file's default location. However, you will have to modify the configuration file if your packages are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], or in multiple instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. Also, if you move the configuration file to a location other than the default location, you will have to modify the Registry key that specifies the file location.  
  
## Configuration File Contents  
 When you install [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], the setup process creates and installs the configuration file for the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service. This configuration file contains the following settings:  
  
-   Packages are sent a stop command when the service stops.  
  
-   The root folders to display for [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] in Object Explorer of [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] are the MSDB and File System folders.  
  
-   The packages in the file system that the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service manages are located in %ProgramFiles%\\Microsoft SQL Server\\110\\DTS\\Packages.  
  
 This configuration file also specifies which msdb database contains the packages that the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service will manage. By default, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is configured to manage packages in the msdb database of the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] that is installed at the same time as [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. If an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is not installed at the same time, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is configured to manage packages in the msdb database of the local, default instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
### Default Configuration File Example  
 The following example shows a default configuration file that specifies the following settings:  
  
-   Packages stop running when the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service stops.  
  
-   The root folders for package storage in [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] are MSDB and File System.  
  
-   The service manages packages that are stored in the msdb database of the local, default instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   The service manages packages that are stored in the file system in the Packages folder.  
  
 **Example of a Default Configuration File**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## Modification of the Configuration File  
 You can modify the configuration file to allow packages to continue running if the service stops, to display additional root folders in Object Explorer, or to specify a different folder or additional folders in the file system to be managed by [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service. For example, you can create additional root folders of type, **SqlServerFolder**, to manage packages in the msdb databases of additional instances of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
> [!NOTE]  
>  Some characters are not valid in folder names. Valid characters for folder names are determined by the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] class **System.IO.Path** and the **GetInvalidFilenameChars** field. The **GetInvalidFilenameChars** field provides a platform\-specific array of characters that cannot be specified in path string arguments passed to members of the **Path** class. The set of invalid characters can vary by file system. Typically, invalid characters are the quotation mark \("\), less than \(\<\) character, and pipe \(|\) character.  
  
 However, you will have to modify the configuration file to manage packages that are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. If you do not update the configuration file, you cannot use **Object Explorer** in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to view packages that are stored in the msdb database on the named instance or the remote instance. If you try to use **Object Explorer** to view these packages, you receive the following error message:  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 To modify the configuration file for the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, you use a text editor.  
  
> [!IMPORTANT]  
>  After you modify the service configuration file, you must restart the service to use the updated service configuration.  
  
### Modified Configuration File Example  
 The following example shows a modified configuration file for [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. This file is for a named instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] called `InstanceName` on a server named `ServerName`.  
  
 **Example of a Modified Configuration File for a Named Instance of SQL Server**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## Modification of the Configuration File Location  
 The Registry key HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\110\\SSIS\\ServiceConfigFile specifies the location and name for the configuration file that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service uses. The default value of the Registry key is C:\\Program Files\\Microsoft SQL Server\\110\\DTS\\Binn\\ MsDtsSrvr.ini.xml. You can update the value of the Registry key to use a different name and location for the configuration file.  
  
> [!CAUTION]  
>  Incorrectly editing the Registry can cause serious problems that may require you to reinstall your operating system. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] cannot guarantee that problems resulting from editing the Registry incorrectly can be resolved. Before editing the Registry, back up any valuable data. For information about how to back up, restore, and edit the Registry, see the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Knowledge Base article, [Description of the Microsoft Windows registry](http://support.microsoft.com/kb/256986).  
  
 The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service loads the configuration file when the service is started. Any changes to the Registry entry require that the service be restarted.  
  
  