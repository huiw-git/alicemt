---
title: View or Change Registered Filters and Word Breakers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
---
# View or Change Registered Filters and Word Breakers
  After any word breakers or filters are installed or uninstalled on a system, the changes do not automatically take effect on server instances. This topic describes how to view the currently registered word breaker or filters and how to register newly installed word breakers and filters on an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
### To view a list of languages whose word breakers are currently registered  
  
1.  Use the [sys.fulltext\_languages](../Topic/sys.fulltext_languages%20\(Transact-SQL\).md) catalog view, as follows:  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### To view a list of the filters that are currently registered  
  
1.  Use the [sp\_help\_fulltext\_system\_components](../Topic/sp_help_fulltext_system_components%20\(Transact-SQL\).md) system stored procedure, as follows:  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### To register newly installed word breakers and filters  
  
1.  Use the [sp\_fulltext\_service](../Topic/sp_fulltext_service%20\(Transact-SQL\).md) system stored procedure to update the list of languages, as follows:  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### To unregister uninstalled word breakers and filters  
  
1.  Use the **sp\_fulltext\_service** to update the list of languages, as follows:  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  Use the **sp\_fulltext\_service** to restart the filter daemon host processes \(fdhost.exe\), as follows:  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### To replace existing word breakers or filters when installing new ones  
  
1.  When preparing to install a DLL file that contains new word breakers or filters, verify that it has a different filename from any of the existing DLL files installed on your server instance.  
  
2.  Copy the new DLL file into the directory containing the standard [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] DLL files for the server instance. The default location is:  
  
     C:\\Program Files\\Microsoft SQL Server\\MSSQL.*instance\_name*\\MSSQL\\Binn  
  
    > [!IMPORTANT]  
    >  We highly recommend that you load only signed and verified components. Also, we recommend that you run the FDHOST Launcher \(MSSQLFDLauncher\) Service with the least possible privileges.  
  
3.  Install the new word breaker or filters.  
  
     **To install and load Microsoft Filter Pack IFilters**  
  
    -   [How to register Microsoft Filter Pack IFilters with SQL Server](http://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  Use **sp\_fulltext\_service** to load newly installed word breakers and filters in the server instance, as follows:  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  Use **sp\_fulltext\_service** to update the list of languages, as follows:  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  Restart the filter daemon host processes \(fdhost.exe\), using **sp\_fulltext\_service** as follows:  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## See Also  
 [Set the Service Account for the Full-text Filter Daemon Launcher](../../Topics\TopicNameNotContainA/Set-the-Service-Account-for-the-Full-text-Filter-Daemon-Launcher.md)   
 [Configure and Manage Filters for Search](../../Topics\TopicNameNotContainA/Configure-and-Manage-Filters-for-Search.md)   
 [Configure and Manage Word Breakers and Stemmers for Search](../../Topics\TopicNameNotContainA/Configure-and-Manage-Word-Breakers-and-Stemmers-for-Search.md)  
  
  