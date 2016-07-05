---
title: Working with SSMA Projects (SybaseToSQL)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
---
# Working with SSMA Projects (SybaseToSQL)
To migrate Sybase Adaptive Server Enterprise (ASE) databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure, you first create an SSMA project. The project is a file that contains metadata about the ASE databases that you want to migrate to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure, metadata about the target instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure that will receive the migrated objects and data, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure connection information, and project settings.  
  
When you open a project, it is disconnected from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure. This lets you work offline. You can reconnect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure. For more information, see [Connecting to SQL Server &#40;SybaseToSQL&#41;](../content/Connecting-to-SQL-Server--SybaseToSQL-.md) \/ [Connecting to Azure SQL DB &#40;SybaseToSQL&#41;](../content/Connecting-to-Azure-SQL-DB--SybaseToSQL-.md).  
  
## Reviewing Default Project Settings  
SSMA contains several options for converting and loading database objects, migrating data, and synchronizing SSMA with ASE and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure. The default settings for these options are appropriate for many users. However, before you create a new SSMA project, you should review the options and, if you want to, change the defaults that will be used for all your new projects.  
  
**To review default project settings**  
  
1.  On the **Tools** menu, select **Default Project Settings**.  
  
2.  Select the project type in **Migration Target Version** drop down for which settings are required to be viewed or changed and then Click **General** tab.  
  
3.  In the left pane, click **Conversion**.  
  
4.  In the right pane, review the options, changing options as necessary. For more information about these options, see [Project Settings &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../content/Project-Settings--Conversion---SybaseToSQL-.md).  
  
5.  Repeat steps 1\-3 for the Migration, SQL Azure, Loading Objects, GUI, and Type Mapping pages.  
  
    -   For information about migration options, see [Project Settings &#40;Migration&#41; &#40;SybaseToSQL&#41;](../content/Project-Settings--Migration---SybaseToSQL-.md).  
  
    -   For information about options for loading objects into [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], see [Project Settings &#40;Synchronization&#41; &#40;SybaseToSQL&#41;](../content/Project-Settings--Synchronization---SybaseToSQL-.md).  
  
    -   For more information about GUI options, see [Project Settings &#40;GUI&#41; &#40;SybaseToSQL&#41;](../content/Project-Settings--GUI---SybaseToSQL-.md).  
  
    -   For more information about data type mapping settings, click [Project Settings &#40;Type Mapping&#41; &#40;SybaseToSQL&#41;](../content/Project-Settings--Type-Mapping---SybaseToSQL-.md).  
  
    -   For more information about SQL Azure options, see [Project Settings &#40;Azure SQL DB &#41; &#40;SybaseToSQL&#41;](../content/Project-Settings--Azure-SQL-DB----SybaseToSQL-.md).  
  
    > [!NOTE]  
    > The SQL Azure settings will be displayed only when you select **Migration to SQL Azure** while creating a project.  
  
## Creating New Projects  
To migrate data from ASE databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure, you must first create a project.  
  
**To create a project**  
  
1.  On the **File** menu, select **New Project**.  
  
    The **New Project** dialog box appears.  
  
2.  In the **Name** box, enter a name for your project.  
  
3.  In the **Location** box, enter or select a folder for the project.  
  
4.  In the **Migration To** drop down, select the version of target [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] used for migration. The options available are:  
  
    -   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] 2016  
  
    -   Azure SQL DB  
  
And then Click **OK**.  
  
## Customizing Project Settings  
In addition to defining default project settings that apply to all new SSMA projects, you can customize the settings for each project. For more information, see [Setting Project Options &#40;SybaseToSQL&#41;](../content/Setting-Project-Options--SybaseToSQL-.md).  
  
When you customize data type mappings between source and target databases, you can define mappings at the project, database, or object level. For more information about type mapping, see [Mapping Sybase ASE and SQL Server Data Types &#40;SybaseToSQL&#41;](../content/Mapping-Sybase-ASE-and-SQL-Server-Data-Types--SybaseToSQL-.md).  
  
## Saving Projects  
When you save a project, SSMA retains the project settings, and optionally the database metadata, to the project file.  
  
**To save a project**  
  
-   On the **File** menu, select **Save Project**.  
  
    If databases within the project have changed or have not been converted, SSMA will prompt you to save metadata into the project. Saving metadata will let you work offline and to send a complete project file to other people, including technical support personnel. If you are prompted to save metadata, do the following:  
  
    1.  For each database that shows a status of **Metadata missing**, select the check box next to the database name.  
  
        Saving metadata might take several minutes. If you do not want to save metadata at this point, do not select any check boxes.  
  
    2.  Click the **Save** button.  
  
        SSMA will parse the Sybase ASE schemas and save the metadata to the project file.  
  
## Opening Projects  
When you open a project, it is disconnected from ASE and from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure. This lets you work offline. To update metadata, load database objects into [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure. To migrate data, you must reconnect to ASE and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure.  
  
**To open a project**  
  
1.  Use one of the following procedures:  
  
    -   On the **File** menu, point to **Recent Projects**, and then select the project you want to open.  
  
    -   On the **File** menu, select **Open Project**, locate the .s2ssproj project file, select the file, and then click **Open**.  
  
2.  To reconnect to ASE, on the **File** menu, select **Reconnect to Sybase**.  
  
3.  To reconnect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure, on the **File** menu, select **Reconnect to SQL Server** \/ **Reconnect to SQL Azure**.  
  
## Next Step  
The next step in the migration process is to [Connect to Sybase ASE](assetId:///a45a2330-9175-4c9e-af38-ef920e350614).  
  
## See Also  
[Migrating Sybase ASE Databases to SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../content/Migrating-Sybase-ASE-Databases-to-SQL-Server---Azure-SQL-DB--SybaseToSQL-.md)  
[Connecting to Sybase ASE &#40;SybaseToSQL&#41;](../content/Connecting-to-Sybase-ASE--SybaseToSQL-.md)  
[Connecting to SQL Server &#40;SybaseToSQL&#41;](../content/Connecting-to-SQL-Server--SybaseToSQL-.md)  
[Connecting to Azure SQL DB &#40;SybaseToSQL&#41;](../content/Connecting-to-Azure-SQL-DB--SybaseToSQL-.md)  
  
