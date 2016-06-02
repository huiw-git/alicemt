---
title: Add, Delete, or Share a Connection Manager in a Package
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f2ba4ea-10be-4c40-9e80-7efcf6ee9655
---
# Add, Delete, or Share a Connection Manager in a Package
  [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes a variety of connection managers for connecting to different data sources, such as relational databases, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] databases, and files in CSV and XML formats. A connection manager can be created at the package level or at the project level. The connection manager created at the project level is available all the packages in the project. Whereas, connection manager created at the package level is available to that specific package.  
  
 You use connection managers that are created at the project level in place of data sources, to share connections to sources. To add a connection manager at the project level, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project must use the project deployment model. When a project is configured to use this model, the **Connection Managers** folder appears in **Solution Explorer**, and the **Data Sources** folder is removed from **Solution Explorer**.  
  
> [!NOTE]  
>  If you want to use data sources in your package, you need to convert the project to the package deployment model.  
>   
>  For more information about the two models, see [Deployment of Projects and Packages](../../Topics\TopicNameNotContainA/Deployment-of-Projects-and-Packages.md). For more information about converting a project to the project deployment model, see [Deploy Projects to Integration Services Server](../../Topics\TopicNameNotContainA/Deploy-Projects-to-Integration-Services-Server.md).  
  
 The following procedures apply to all types of connection managers and describe how to do the following tasks:  
  
-   [To add a connection manager when creating a package](#wizard)  
  
-   [To add a connection manager to an existing package](#package)  
  
-   [To add a connection manager at the project level](#project)  
  
-   [To create a parameter for a connection manager property](#parameter)  
  
-   [To delete a connection manager from a package](#DeletePackageLevel)  
  
-   [To delete a shared connection manager (project level connection manager)](#DeleteProjectLevel)  
  
##  <a name="wizard"></a> To add a connection manager when creating a package  
  
-   Use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard  
  
     In addition to creating and configuring a connection manager, the wizard also helps you create and configure the sources and destinations that use the connection manager. For more information, see [Create Packages in SQL Server Data Tools](../../Topics\TopicNameNotContainA/Create-Packages-in-SQL-Server-Data-Tools.md).  
  
##  <a name="package"></a> To add a connection manager to an existing package  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it  
  
3.  In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the **Control Flow** tab, the **Data Flow** tab, or the **Event Handler** tab to make the **Connection Managers** area available.  
  
4.  Right\-click anywhere in the **Connection Managers** area, and then do one of the following:  
  
    -   Click the connection manager type to add to the package.  
  
         —or—  
  
    -   If the type that you want to add is not listed, click **New Connection** to open the **Add SSIS Connection Manager** dialog box, select a connection manager type, and then click **OK**.  
  
     The custom dialog box for the selected connection manager type opens. For more information about connection manager types and the options that are available, see the following options table.  
  
    |Connection manager|Options|  
    |------------------------|-------------|  
    |[ADO Connection Manager](../../Topics\TopicNameNotContainA/ADO-Connection-Manager.md)|[Configure OLE DB Connection Manager](../../Topics\TopicNameNotContainA/Configure-OLE-DB-Connection-Manager.md)|  
    |[ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/ADO.NET-Connection-Manager.md)|[Configure ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/Configure-ADO.NET-Connection-Manager.md)|  
    |[Analysis Services Connection Manager](../../Topics\TopicNameNotContainA/Analysis-Services-Connection-Manager.md)|[Add Analysis Services Connection Manager Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Add-Analysis-Services-Connection-Manager-Dialog-Box-UI-Reference.md)|  
    |[Excel Connection Manager](../../Topics\TopicNameNotContainA/Excel-Connection-Manager.md)|[Excel Connection Manager Editor](../../Topics\TopicNameNotContainA/Excel-Connection-Manager-Editor.md)|  
    |[File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md)|[File Connection Manager Editor](../../Topics\TopicNameNotContainA/File-Connection-Manager-Editor.md)|  
    |[Multiple Files Connection Manager](../../Topics\TopicNameNotContainA/Multiple-Files-Connection-Manager.md)|[Add File Connection Manager Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Add-File-Connection-Manager-Dialog-Box-UI-Reference.md)|  
    |[Flat File Connection Manager](../../Topics\TopicNameNotContainA/Flat-File-Connection-Manager.md)|[Flat File Connection Manager Editor &#40;General Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(General%20Page\).md)<br /><br /> [Flat File Connection Manager Editor &#40;Columns Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)<br /><br /> [Flat File Connection Manager Editor &#40;Advanced Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)<br /><br /> [Flat File Connection Manager Editor &#40;Preview Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)|  
    |[Multiple Flat Files Connection Manager](../../Topics\TopicNameNotContainA/Multiple-Flat-Files-Connection-Manager.md)|[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(General%20Page\).md)<br /><br /> [Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)<br /><br /> [Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)<br /><br /> [Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)|  
    |[FTP Connection Manager](../../Topics\TopicNameNotContainA/FTP-Connection-Manager.md)|[FTP Connection Manager Editor](../../Topics\TopicNameNotContainA/FTP-Connection-Manager-Editor.md)|  
    |[HTTP Connection Manager](../../Topics\TopicNameNotContainA/HTTP-Connection-Manager.md)|[HTTP Connection Manager Editor &#40;Server Page&#41;](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Server%20Page\).md)<br /><br /> [HTTP Connection Manager Editor &#40;Proxy Page&#41;](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Proxy%20Page\).md)|  
    |[MSMQ Connection Manager](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager.md)|[MSMQ Connection Manager Editor](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager-Editor.md)|  
    |[ODBC Connection Manager](../../Topics\TopicNameNotContainA/ODBC-Connection-Manager.md)|[ODBC Connection Manager UI Reference](../../Topics\TopicNameNotContainA/ODBC-Connection-Manager-UI-Reference.md)|  
    |[OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md)|[Configure OLE DB Connection Manager](../../Topics\TopicNameNotContainA/Configure-OLE-DB-Connection-Manager.md)|  
    |[SMO Connection Manager](../../Topics\TopicNameNotContainA/SMO-Connection-Manager.md)|[SMO Connection Manager Editor](../../Topics\TopicNameNotContainA/SMO-Connection-Manager-Editor.md)|  
    |[SMTP Connection Manager](../../Topics\TopicNameNotContainA/SMTP-Connection-Manager.md)|[SMTP Connection Manager Editor](../../Topics\TopicNameNotContainA/SMTP-Connection-Manager-Editor.md)|  
    |[SQL Server Compact Edition Connection Manager](../../Topics\TopicNameNotContainA/SQL-Server-Compact-Edition-Connection-Manager.md)|[SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;](../Topic/SQL%20Server%20Compact%20Edition%20Connection%20Manager%20Editor%20\(Connection%20Page\).md)<br /><br /> [SQL Server Compact Edition Connection Manager Editor &#40;All Page&#41;](../Topic/SQL%20Server%20Compact%20Edition%20Connection%20Manager%20Editor%20\(All%20Page\).md)|  
    |[WMI Connection Manager](../../Topics\TopicNameNotContainA/WMI-Connection-Manager.md)|[WMI Connection Manager Editor](../../Topics\TopicNameNotContainA/WMI-Connection-Manager-Editor.md)|  
  
     The **Connection Managers** area lists the added connection manager.  
  
5.  Optionally, right\-click the connection manager, click **Rename**, and then modify the default name of the connection manager.  
  
6.  To save the updated package, click **Save Selected Item** on the **File** menu.  
  
##  <a name="project"></a> To add a connection manager at the project level  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project.  
  
2.  In **Solution Explorer**, right\-click **Connection Managers**, and click **New Connection Manager**.  
  
3.  In the **Add SSIS Connection Manager** dialog box, select the type of connection manager, and then click **Add**.  
  
     The custom dialog box for the selected connection manager type opens. For more information about connection manager types and the options that are available, see the following options table.  
  
    |Connection manager|Options|  
    |------------------------|-------------|  
    |[ADO Connection Manager](../../Topics\TopicNameNotContainA/ADO-Connection-Manager.md)|[Configure OLE DB Connection Manager](../../Topics\TopicNameNotContainA/Configure-OLE-DB-Connection-Manager.md)|  
    |[ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/ADO.NET-Connection-Manager.md)|[Configure ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/Configure-ADO.NET-Connection-Manager.md)|  
    |[Analysis Services Connection Manager](../../Topics\TopicNameNotContainA/Analysis-Services-Connection-Manager.md)|[Add Analysis Services Connection Manager Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Add-Analysis-Services-Connection-Manager-Dialog-Box-UI-Reference.md)|  
    |[Excel Connection Manager](../../Topics\TopicNameNotContainA/Excel-Connection-Manager.md)|[Excel Connection Manager Editor](../../Topics\TopicNameNotContainA/Excel-Connection-Manager-Editor.md)|  
    |[File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md)|[File Connection Manager Editor](../../Topics\TopicNameNotContainA/File-Connection-Manager-Editor.md)|  
    |[Multiple Files Connection Manager](../../Topics\TopicNameNotContainA/Multiple-Files-Connection-Manager.md)|[Add File Connection Manager Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Add-File-Connection-Manager-Dialog-Box-UI-Reference.md)|  
    |[Flat File Connection Manager](../../Topics\TopicNameNotContainA/Flat-File-Connection-Manager.md)|[Flat File Connection Manager Editor &#40;General Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(General%20Page\).md)<br /><br /> [Flat File Connection Manager Editor &#40;Columns Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)<br /><br /> [Flat File Connection Manager Editor &#40;Advanced Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)<br /><br /> [Flat File Connection Manager Editor &#40;Preview Page&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)|  
    |[Multiple Flat Files Connection Manager](../../Topics\TopicNameNotContainA/Multiple-Flat-Files-Connection-Manager.md)|[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(General%20Page\).md)<br /><br /> [Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)<br /><br /> [Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)<br /><br /> [Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)|  
    |[FTP Connection Manager](../../Topics\TopicNameNotContainA/FTP-Connection-Manager.md)|[FTP Connection Manager Editor](../../Topics\TopicNameNotContainA/FTP-Connection-Manager-Editor.md)|  
    |[HTTP Connection Manager](../../Topics\TopicNameNotContainA/HTTP-Connection-Manager.md)|[HTTP Connection Manager Editor &#40;Server Page&#41;](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Server%20Page\).md)<br /><br /> [HTTP Connection Manager Editor &#40;Proxy Page&#41;](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Proxy%20Page\).md)|  
    |[MSMQ Connection Manager](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager.md)|[MSMQ Connection Manager Editor](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager-Editor.md)|  
    |[ODBC Connection Manager](../../Topics\TopicNameNotContainA/ODBC-Connection-Manager.md)|[ODBC Connection Manager UI Reference](../../Topics\TopicNameNotContainA/ODBC-Connection-Manager-UI-Reference.md)|  
    |[OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md)|[Configure OLE DB Connection Manager](../../Topics\TopicNameNotContainA/Configure-OLE-DB-Connection-Manager.md)|  
    |[SMO Connection Manager](../../Topics\TopicNameNotContainA/SMO-Connection-Manager.md)|[SMO Connection Manager Editor](../../Topics\TopicNameNotContainA/SMO-Connection-Manager-Editor.md)|  
    |[SMTP Connection Manager](../../Topics\TopicNameNotContainA/SMTP-Connection-Manager.md)|[SMTP Connection Manager Editor](../../Topics\TopicNameNotContainA/SMTP-Connection-Manager-Editor.md)|  
    |[SQL Server Compact Edition Connection Manager](../../Topics\TopicNameNotContainA/SQL-Server-Compact-Edition-Connection-Manager.md)|[SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;](../Topic/SQL%20Server%20Compact%20Edition%20Connection%20Manager%20Editor%20\(Connection%20Page\).md)<br /><br /> [SQL Server Compact Edition Connection Manager Editor &#40;All Page&#41;](../Topic/SQL%20Server%20Compact%20Edition%20Connection%20Manager%20Editor%20\(All%20Page\).md)|  
    |[WMI Connection Manager](../../Topics\TopicNameNotContainA/WMI-Connection-Manager.md)|[WMI Connection Manager Editor](../../Topics\TopicNameNotContainA/WMI-Connection-Manager-Editor.md)|  
  
     The connection manager you added will show up under the **Connections Managers** node in the **Solution Explorer**. It will also appear in the **Connection Managers** tab in the **SSIS Designer** window for all the packages in the project. The name of the connection manager in this tab will have a **\(project\)** prefix in order to differentiate this project level connection manager from the package level connection managers.  
  
4.  Optionally, right\-click the connection manager in the **Solution Explorer** window under **Connection Managers** node \(or\) in the **Connection Managers** tab of the **SSIS Designer** window, click **Rename**, and then modify the default name of the connection manager.  
  
    > [!NOTE]  
    >  In the **Connection Managers** tab of the **SSIS Designer** window, you won’t be able to overwrite the **\(project\)** prefix from the connection manager name. This is by design.  
  
##  <a name="parameter"></a> To create a parameter for a connection manager property  
  
1.  In the **Connection Managers** area, right\-click the connection manager that you want to create a parameter for and then click **Parameterize**.  
  
2.  Configure the parameter settings in the **Parameterize** dialog box. For more information, see [Parameterize Dialog Box](../../Topics\TopicNameNotContainA/Parameterize-Dialog-Box.md).  
  
##  <a name="DeletePackageLevel"></a> To delete a connection manager from a package  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it.  
  
3.  In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the **Control Flow** tab, the **Data Flow** tab, or the **Event Handler** tab to make the **Connection Managers** area available.  
  
4.  Right\-click the connection manager that you want to delete, and then click **Delete**.  
  
     If you delete a connection manager that a package element, such as an Execute SQL task or an OLE DB source, uses, you will experience the following results:  
  
    -   An error icon appears on the package element that used the deleted connection manager.  
  
    -   The package fails to validate.  
  
    -   The package cannot be run.  
  
5.  To save the updated package, click **Save Selected Items** on the **File** menu.  
  
##  <a name="DeleteProjectLevel"></a> To delete a shared connection manager \(project level connection manager\)  
  
1.  To delete a project\-level connection manager, right\-click the connection manager under **Connection Managers** node in the **Solution Explorer** window, and then click **Delete**. [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)] displays the following warning message:  
  
    > [!WARNING]  
    >  When you delete a project connection manager, packages that use the connection manager might not run. You cannot undo this action. Do you want to delete the connection manager?  
  
2.  Click OK to delete the connection manager or Cancel to keep it.  
  
    > [!NOTE]  
    >  You can also delete a project level connection manager from the **Connection Manager** tab of the **SSIS Designer** window opened for any package in the project. You do so by right\-clicking the connection manager in the tab and then by clicking **Delete**.  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)   
 [Set the Properties of a Connection Manager](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Connection-Manager.md)  
  
  