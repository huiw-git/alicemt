---
title: Upgrade SQLCLR Assemblies After .NET Framework Update
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
---
# Upgrade SQLCLR Assemblies After .NET Framework Update
  [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) is a collection of SQL Common Language Runtime \(SQLCR\) routines that reference Microsoft .NET Framework 4 assemblies. When you install any .NET Framework updates on your computer that affect any such referenced .NET Framework assembly, it leads to a change in the Module Version ID \(MVID\) of the assembly in the Global Assembly Cache \(GAC\). This causes a mismatch between the MVIDs of the referenced assembly in GAC and the assembly in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 If the .NET Framework update requires you to restart the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] computer, the affected SQLCLR assemblies are upgraded automatically to fix the MVID mismatch issue on restarting the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] computer. However, for .NET Framework updates that do not require you to restart your [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] computer, an error occurs due to the mismatch in the MVIDs of the assemblies when you try to connect to a [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] using a [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]:  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe –upgradedlls.  
```  
  
 To fix this issue, the affected SQLCLR assemblies in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] must be upgraded. You can do so by running the DQSInstaller.exe file with the **upgradedlls** command line parameter to skip recreating the DQS databases, and just upgrade the affected assemblies. This ensures that your knowledge bases, data quality projects, and any other data in DQS are preserved.  
  
## Prerequisites  
  
-   You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] computer.  
  
-   Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] is installed.  
  
### To upgrade SQLCLR Assemblies  
  
1.  Start Command Prompt.  
  
2.  At the command prompt, change your directory to the location where DQSInstaller.exe is available. If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  At the command prompt, type the following command, and press ENTER:  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  Rest of the steps are same as steps 2\-6 in the [Run DQSInstaller.exe from Start Screen, Start Menu or Windows Explorer](../../Topics\TopicNameNotContainA/Run-DQSInstaller.exe-to-Complete-Data-Quality-Server-Installation.md) section in [Run DQSInstaller.exe to Complete Data Quality Server Installation](../../Topics\TopicNameNotContainA/Run-DQSInstaller.exe-to-Complete-Data-Quality-Server-Installation.md).  
  
## See Also  
 [Install Data Quality Services](../../Topics\TopicNameNotContainA/Install-Data-Quality-Services.md)   
 [Upgrade DQS Databases Schema After Installing SQL Server Update](../../Topics\TopicNameNotContainA/Upgrade-DQS-Databases-Schema-After-Installing-SQL-Server-Update.md)  
  
  