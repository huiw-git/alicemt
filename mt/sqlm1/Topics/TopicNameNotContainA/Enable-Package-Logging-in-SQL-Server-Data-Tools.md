---
title: Enable Package Logging in SQL Server Data Tools
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b69a8593-5bb0-4f04-87d2-f8e7bd7eb4fc
---
# Enable Package Logging in SQL Server Data Tools
  This procedure describes how to add logs to a package, configure package\-level logging, and save the logging configuration to an XML file. You can add logs only at the package level, but the package does not have to perform logging to enable logging in the containers that the package includes.  
  
> [!IMPORTANT]  
>  If you deploy the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server, the logging level that you set for the package execution overrides the package logging that you configure using [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
 By default, the containers in the package use the same logging configuration as their parent container. For information about setting logging options for individual containers, see [Configure Logging by Using a Saved Configuration File](../../Topics\TopicNameContainA/Configure-Logging-by-Using-a-Saved-Configuration-File.md).  
  
### To enable logging in a package  
  
1.  In [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  On the **SSIS** menu, click **Logging**.  
  
3.  Select a log provider in the **Provider type** list, and then click **Add**.  
  
4.  In the **Configuration** column, select a connection manager or click **\<New connection\>** to create a new connection manager of the appropriate type for the log provider. Depending on the selected provider, use one of the following connection managers:  
  
    -   For Text files, use a File connection manager. For more information, see [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md)  
  
    -   For [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], use a File connection manager.  
  
    -   For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], use an OLE DB connection manager. For more information, see [OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md).  
  
    -   For Windows Event Log, do nothing. [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] automatically creates the log.  
  
    -   For XML files, use a File connection manager.  
  
5.  Repeat steps 3 and 4 for each log to use in the package.  
  
    > [!NOTE]  
    >  A package can use more than one log of each type.  
  
6.  Optionally, select the package\-level check box, select the logs to use for package\-level logging, and then click the **Details** tab.  
  
7.  On the **Details** tab, select **Events** to log all log entries, or clear **Events** to select individual events.  
  
8.  Optionally, click **Advanced** to specify which information to log.  
  
    > [!NOTE]  
    >  By default, all information is logged.  
  
9. On the **Details** tab, click **Save.** The **Save As** dialog box appears. Locate the folder in which to save the logging configuration, type a file name for the new log configuration, and then click **Save**.  
  
10. Click **OK**.  
  
11. To save the updated package, click **Save Selected Items** on the **File** menu.  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md)   
 [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md)  
  
  