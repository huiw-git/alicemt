---
title: Install Data Quality Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 486e4216-a946-4c6e-828c-61bc905f7ec1
---
# Install Data Quality Services
  [!INCLUDE[ssDQSnoversionLong](../../Token\Other/ssDQSnoversionLong_md.md)] \(DQS\) contains the following two components: **[!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)]** and **[!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]**.  
  
|DQS Component|Description|  
|-------------------|-----------------|  
|[!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)]|[!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] is installed on top of the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Database Engine, and includes three databases: DQS\_MAIN, DQS\_PROJECTS, and DQS\_STAGING\_DATA. DQS\_MAIN contains DQS stored procedures, the DQS engine, and published knowledge bases. DQS\_PROJECTS contains the data quality project information. DQS\_STAGING\_DATA is the staging area where you can copy your source data to perform DQS operations, and then export your processed data.|  
|[!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]|[!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] is a standalone application that enables you to connect to [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)], and provides you with a highly\-intuitive graphical user interface to perform data\-quality operations, and other administrative tasks related to DQS.|  
  
> [!IMPORTANT]  
>  Apart from the above two DQS components, you can also:  
>   
>  Use the DQS Cleansing Transformation in Integration Services that performs data cleansing within the Integration Services packaging process, and is automatically installed when you install Integration Services. For information about installing Integration Services, see [Install Integration Services](../../Topics\TopicNameNotContainA/Install-Integration-Services.md).  
>   
>  Enable DQS integration in Master Data Services to use the DQS matching functionality in the Master Data Services Add\-in for Excel. For more information, see [Enable Data Quality Services Integration with Master Data Services](../../Topics\TopicNameNotContainA/Enable-Data-Quality-Services-Integration-with-Master-Data-Services.md).  
  
 DQS installation is a three\-part process:  
  
-   [Pre-Installation Tasks](#PreInstallationTasks): Verify system requirements before you install DQS.  
  
-   [Data Quality Services Installation Tasks](#DQSInstallation): Install DQS by using SQL Server Setup.  
  
-   [Post-Installation Tasks](#PostInstallationTasks): Perform these tasks after finishing with the SQL Server Setup to finish installing DQS.  
  
> [!NOTE]  
>  This topic does not include instructions for running Setup from the command line. For information about command\-line options for installing [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] and client, see [Feature Parameters](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md) in [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
##  <a name="PreInstallationTasks"></a> Pre\-Installation Tasks  
 Before installing DQS, make sure that your computer meets the minimum system requirements. The following table provides information about the minimum system requirements for the DQS components:  
  
|DQS Component|Minimum System Requirements|  
|-------------------|---------------------------------|  
|[!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)]|Memory \(RAM\): Minimum: 2 GB \/ Recommended: 4 GB or more<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Database Engine. For more information, see [Install SQL Server Database Engine](../../Topics\TopicNameNotContainA/Install-SQL-Server-Database-Engine.md).|  
|[!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]|.NET Framework 4.0 \(installed during the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] installation, if not already installed\)<br /><br /> Internet Explorer 6.0 SP1 or later|  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] and [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] can be installed on the same computer, or different computers. Both the components can be installed independently of each other, and in any sequence. However, to use [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)], you will need a [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] installed to connect to.  
>   
>  You can connect to the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] version of [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] using either the current or earlier version of [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] and DQS Cleansing Transformation. For information about upgrading your existing version of DQS to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], see [Upgrade Data Quality Services](../../Topics\TopicNameNotContainA/Upgrade-Data-Quality-Services.md).  
>   
>  Although Microsoft Excel is not a prerequisite for installing Data Quality Client, Microsoft Excel 2003 or later must be installed on the Data Quality Client computer to perform various operations in the client application such as importing domain values from an excel file or mapping to the source data in an Excel file for knowledge discovery, cleansing, or matching activities.  
  
 For detailed information about the minimum system requirements for installing [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], see [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md).  
  
##  <a name="DQSInstallation"></a> Data Quality Services Installation Tasks  
 You have to use the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Setup to install DQS components. When you run the SQL Server Setup, you have to go through a series of installation wizard pages to select appropriate options based on your requirements. The following table lists only those pages in the installation wizard where the options that you select will affect your installation of DQS:  
  
|Page|Action|  
|----------|------------|  
|Feature Selection|Select:<br /><br /> **Data Quality Services** under **Database Engine Services** to install the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)]. <br />If you select the **Data Quality Services** check box, SQL Server Setup will copy an installer file, DQSInstaller.exe, under the SQL Server instance directory on your computer. You must run this file after you have completed the SQL Server Setup to *complete* the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] installation. Also, you must perform some additional steps to configure your [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] before you can use it. For more information, see [Post-Installation Tasks](#PostInstallationTasks).<br /><br /> **Data Quality Client** to install [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)].<br /><br /> \(Recommended\) **Management Tools – Complete** under **Management Tools – Basic** to install [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. It provides you a graphical user interface to manage your SQL Server instance, and will aid you in performing additional tasks post installation as listed in the next section.|  
|Database Engine Configuration|Click **Add Current User** to add your user Windows account to the sysadmin fixed server role. This is required for you to be able to run the DQSInstaller.exe file later to complete the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] installation.|  
  
##  <a name="PostInstallationTasks"></a> Post\-Installation Tasks  
 After you complete the SQL Server installation wizard, you must perform additional steps mentioned in this section to complete your [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] installation, configure it, and then use it.  
  
1.  To complete the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] installation, run the DQSInstaller.exe file. On running the DQSInstaller.exe file:  
  
    -   The DQS\_MAIN, DQS\_PROJECTS, and DQS\_STAGING\_DATA databases are created.  
  
    -   The \#\#MS\_dqs\_db\_owner\_login\#\# and \#\#MS\_dqs\_service\_login\#\# logins are created.  
  
    -   The dqs\_administrator, dqs\_kb\_editor, and dqs\_kb\_operator roles are created in the DQS\_MAIN database.  
  
    -   The DQInitDQS\_MAIN stored procedure is created in the master database.  
  
    -   DQS\_install.log file is typically created in the C:\\Program Files\\Microsoft SQL Server\\MSSQL13.*\<instance\_name\>*\\MSSQL\\Log folder. The file contains information about the actions performed on running the DQSInstaller.exe file.  
  
    -   If a Master Data Services database is present in the same SQL Server instance as [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)], a user mapped to the Master Data Services login is created, and is granted the dqs\_administrator role on the DQS\_MAIN database.  
  
     This completes the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] installation.  
  
     For more information see [Run DQSInstaller.exe to Complete Data Quality Server Installation](../../Topics\TopicNameNotContainA/Run-DQSInstaller.exe-to-Complete-Data-Quality-Server-Installation.md).  
  
2.  Grant DQS Roles to Users:  
  
     To log on to [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] using [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)], a user must have any of the following three roles on the DQS\_MAIN database:  
  
    -   **dqs\_administrator**  
  
    -   **dqs\_kb\_editor**  
  
    -   **dqs\_kb\_operator**  
  
     By default, if your user account is a member of the sysadmin fixed server role, you can log on to [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] using [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] even if none of the DQS roles are granted to your user account. For information about the three DQS roles, see [DQS Security](../../Topics\TopicNameNotContainA/DQS-Security.md).  
  
     For more information see [Grant DQS Roles to Users](../../Topics\TopicNameNotContainA/Grant-DQS-Roles-to-Users.md).  
  
    > [!NOTE]  
    >  The three DQS roles are not available for the DQS\_PROJECTS and DQS\_STAGING\_DATA databases.  
  
3.  Make your data available for DQS operations. Make sure that you can access your source data for the DQS operations, and can export the processed data to a table in a database.  
  
     For more information see  
                    [Access Data for the DQS Operations](../../Topics\TopicNameNotContainA/Access-Data-for-the-DQS-Operations.md).  
  
## See Also  
 [Video: Install and Configure DQS](http://go.microsoft.com/fwlink/?LinkId=238241)   
 [Upgrade SQLCLR Assemblies After .NET Framework Update](../../Topics\TopicNameNotContainA/Upgrade-SQLCLR-Assemblies-After-.NET-Framework-Update.md)   
 [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](../../Topics\TopicNameNotContainA/Export-and-Import-DQS-Knowledge-Bases-Using-DQSInstaller.exe.md)   
 [Upgrade Data Quality Services](../../Topics\TopicNameNotContainA/Upgrade-Data-Quality-Services.md)   
 [Remove Data Quality Server Objects](../../Topics\TopicNameNotContainA/Remove-Data-Quality-Server-Objects.md)   
 [Install SQL Server 2016 Business Intelligence Features](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-Business-Intelligence-Features.md)   
 [Uninstall SQL Server 2016](../../Topics\TopicNameNotContainA/Uninstall-SQL-Server-2016.md)   
 [Data Quality Services](../../Topics\TopicNameNotContainA/Data-Quality-Services.md)   
 [Troubleshoot Installation and Configuration Issues in DQS](http://social.technet.microsoft.com/wiki/contents/articles/3776.aspx)  
  
  