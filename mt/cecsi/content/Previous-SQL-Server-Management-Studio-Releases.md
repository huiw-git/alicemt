---
title: Previous SQL Server Management Studio Releases
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f593c3-8b76-4c12-963a-31d35f2fb294
manager: jeffreyg
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Previous SQL Server Management Studio Releases
  
The following previous releases of SQL Server Management Studio are available.
  
### ![download](../content/media/download.png) [SQL Server Management Studio June 2016 release](http://go.microsoft.com/fwlink/?LinkID=799832)

June 1, 2016 | Version number: 13.0.15000.23

**Features**  
New streamlined SSMS installer. Standalone SSMS releases. Automatic check for updates. A new Quick Find dialog. SSMS built on the Visual Studio 2015 shell, and many more.   
[More information available in the SSMS changelog.](../content/SQL-Server-Management-Studio---Changelog--SSMS-.md)

**Known Issues** 
1. **PowerShell script generation from the Always Encrypted wizard is currently disabled.**
A fix for this issue will be available in a subsequent monthly SSMS update.
2. **The 'Encrypt Columns' context menu item in Object Explorer is disabled for tables and columns when you are connected to Azure SQL Database.** A fix for this issue will be available in a subsequent monthly SSMS update. As a workaround, right-click your database in Object Explorer, select 'Tasks', and choose 'Encrypt Columns' to encrypt Azure SQL Database columns and tables.
3. **SSMS can only connect to SQL Server 2016 Integrated Services (SSIS 2016) instances.** There is a known compatibility limitation with SQL Server Integration Services that prevents connecting to previous versions.
As a workaround for this problem, you can connect to your SQL Server Integration Service instance by using the SSMS release aligned with your SSIS instance.
4. **SSMS won't save maintenance plans for SQL Server 2008 R2 and earlier SQL Server versions.** We are working on a fix for this issue. In the meantime, you can use the SSMS 2014 release below to save the maintenance plans.
5. **SQL Server Configuration Manager will fail to launch if there is no SQL Server installed on the client machine.** If you do not have SQL Server installed on your client machine and launch SQL Server Configuration Manager, you will receive the 'Cannot connect to WMI provider' error. As a workaround:
    * Open a command prompt as Administrator.
    * Run the Mofcomp tool using the following command:  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * After you run the Mofcomp tool, run the following commands to restart the WMI service for the changes to take effect:  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**Fixes**  
1. Quick find dialog in SSMS that is better integrated into the current document and allows searching via regular expressions ([Microsoft Connect item #2735513](https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/)).
2. Bug fix in SSMS context-sensitive F1 help to correctly display help documents and articles.
3. Bug fix in Query Data Store 'Regressed Queries' view that caused SSMS to crash when scrolling.
4. Bug fix in Excel Analysis Services OLEDB connector to allow connections from Excel 2016 to SQL Server Analysis Services.
5. Bug fix in SSMS Connection dialog to show the connection dialog on the same monitor as the main SSMS window in multi-monitor systems ([Microsoft Connect item #724909)](https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/).
6. Bug fixes in Always Encrypted experience. Fixed bug where Always Encrypted menu option was not enabled correctly for Stretch databases. Also fixed bug in the Always Encrypted wizard where it was not properly using the SafeNet (Luna SA) HSM provider.

---
### ![download](../content/media/download.png) [SQL Server Management Studio 2014 SP1](http://download.microsoft.com/download/1/5/6/156992E6-F7C7-4E55-833D-249BD2348138/ENU/x86/SQLManagementStudio_x86_ENU.exe)

May 14, 2015 | Version number: 12.0.4100.1

**Features**  
Improved Azure SQL Database support with new open in management portal menu, table designer integration, and more.   
[More information available in the release notes](https://support.microsoft.com/en-us/kb/3058865).

**Known Issues**  
N/A

**Fixes**
1. SSMS Crashes during Movement of Maintenance Plan tasks if the Maintenance Plan name and the first SUB_PLAN name are the same.
2. You cannot debug a stored procedure that calls sp_executesql in SQL Server Management Studio (SSMS). When F11 is pressed, you receive an 'Object reference not set to an instance of object' error message ([Microsoft Connect item #736509](https://connect.microsoft.com/SQLServer/feedback/details/736509/sql-server-2012-rtm-management-studio-cannot-debug-sp-executesql)).
3. SSMS does not fully manage Full-Text in SQL Server Express ([Microsoft Connect item #740181](https://connect.microsoft.com/SQLServer/feedback/details/740181/management-studio-does-not-fully-manage-full-text-in-sql-server-express)).
4. SSMS handles Numbered Stored procedures inconsistently [(Microsoft Connect item #764197](https://connect.microsoft.com/SQLServer/feedback/details/764197/ssms-2012-inconsistently-handles-numbered-procedures)).
5. SSMS occasionally crashes on close, which then causes it to automatically restart ([Microsoft Connect item #774317](https://connect.microsoft.com/SQLServer/feedback/details/774317/sql-server-management-studio-2012-2014-crashes-when-closing)).
6. Create script duplicates the statements when scripting column level permissions in SSMS ([Microsoft Connect item #797967](https://connect.microsoft.com/SQLServer/feedback/details/797967/ssms-create-script-duplicates-the-statements-for-grant-or-deny-column-permissions)).
7. SSMS may crash when you try to refresh the SSMS window icon on the task bar ([Microsoft Connect item #799430](https://connect.microsoft.com/SQLServer/feedback/details/799430/ssms-2012-sp-1-cu-5-installed-crash-when-enforce-refresh-on-connect)).

---
### ![download](../content/media/download.png) [SQL Server Management Studio 2012 SP3](http://download.microsoft.com/download/F/6/7/F673709C-D371-4A64-8BF9-C1DD73F60990/ENU/x86/SQLManagementStudio_x86_ENU.exe)  
  
November 21, 2015 | Version number: 11.0.6020.0

**Features**  
Full\-feature SSMS express editions. Code snippets. Column store indexes, and more.  
[More information available in the release notes.](https://support.microsoft.com/en-us/kb/3072779)
 
**Known Issues**  
N/A

**Fixes**
1. Missing columns can't be indicated in the error message when you import data by using Import and Export Wizard.
2. "Unable to create restore plan due to break in the LSN chain" error when you restore differential backup in SSMS

---
### Additional Downloads  
For a list of all SQL Server Management Studio downloads, search the [Microsoft Download Center](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
For the latest release of SQL Server Management Studio, see [Download SQL Server Management Studio &#40;SSMS&#41;](../content/Download-SQL-Server-Management-Studio--SSMS-.md).  

---  
## Related resources
[Update center for Microsoft SQL Server](https://technet.microsoft.com/sqlserver/ff803383.aspx)   
[SQL Server Management Studio quick start](assetId:///d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[SQL Server Management Studio forum](https://social.msdn.microsoft.com/forums/en-us/home?forum=sqltools)  

  
