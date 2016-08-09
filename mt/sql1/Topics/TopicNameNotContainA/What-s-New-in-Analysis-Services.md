---
title: "What&#39;s New in Analysis Services"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
caps.latest.revision: 93
caps.handback.revision: 0
manager: mblythe
---
# What&#39;s New in Analysis Services
[!INCLUDE[ssASCurrent](../../Topics/TopicNameContainA/tokens/ssASCurrent_md.md)] includes many new enhancements providing improved performance, easier solution authoring, automated database management,   enhanced relationships with bi-directional cross filtering, parallel partition processing, and much more.  
  
 At the heart of most enhancements for this release  is the new 1200 compatibility level. This new compatibility level is only available in [!INCLUDE[ssASCurrent](../../Topics/TopicNameContainA/tokens/ssASCurrent_md.md)]. In order to author solutions  
  
 [!INCLUDE[ssASCurrent](../../Topics/TopicNameContainA/tokens/ssASCurrent_md.md)] feature updates are released incrementally as cumulative and consecutive updates to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] Preview. The latest release is **RC3** (Release Candidate 3).  
  
 Visit the [Analysis Services team blog](https://blogs.msdn.microsoft.com/analysisservices/) for a more detailed introduction to features in this release.  
  
> [!NOTE]  
>  [Preview releases of Analysis Services](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) work best when  server, client tools (SSDT and SSMS), and data providers (especially AMO) are from the same build.  Server software is upgraded via SQL Server Setup. Tools are upgraded when you install a newer update over an existing installation. If you have a custom AMO-dependent application, you might need to install an updated version of AMO. For instructions, see [Install Analysis Services data providers (AMO, ADOMD.NET, MSOLAP)](../../Topics/TopicNameNotContainA/Install-Analysis-Services-data-providers--AMO--ADOMD.NET--MSOLAP-.md).  
  
## PowerShell for Tabular models  
 This release includes PowerShell enhancements for Tabular models created at compatibility level (1200). You can use all of the applicable cmdlets, plus cmdlets specific to Tabular mode: [Invoke-ProcessASDatabase](../../Topics/TopicNameNotContainA/Invoke-ProcessASDatabase.md) and [Invoke-ProcessTable cmdlet](../../Topics/TopicNameNotContainA/Invoke-ProcessTable-cmdlet.md).  
  
## SSIS Tasks for Tabular models  
 SSIS tasks and destinations against a SQL Server 2016 tabular model use Tabular object representations instead of multidimensional. For example, in the latest SSDT, when you select objects to process, the Processing Task will automatically detect it is a Tabular model and show Tabular objects instead of measuregroups and dimensions.  
  
## Microsoft.AnalysisServices.Tabular namespace for Tabular 1200 programmability in AMO  
 Analysis Services Management objects is updated to include a new Tabular namespace for managing a Tabular instance of SQL Server 2016 Analysis Services (at compatibility level 1200), as well as provide the data definition language for creating or modifying Tabular models programmatically. Visit [Microsoft.AnalysisServices.Tabular](assetId:///4d6733fb-5736-4995-a3cf-fbc0380cbf5f) to read up on the API.  
  
## Display folders  
 Display folders are now available for tabular models at 1200 compatibility level. Defined in SQL Server Data Tools and rendered in client applications like Excel or Power BI Desktop, display folders help you organize large numbers of measures into individual folders, adding a visual hierarchy for easier navigation in field lists.  
  
## Pasted tables  
 It's now possible to upgrade an 1100 or 1103 Tabular model to 1200 when the model contains pasted tables. We recommend using [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)] to upgrade a model. In SSDT, set **CompatibilityLevel** to 1200 and then deploy to a [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] instance of [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]. See [Compatibility Level for Tabular models in Analysis Services](../../Topics/TopicNameNotContainA/Compatibility-Level-for-Tabular-models-in-Analysis-Services.md) for details.  
  
## SSMS scripting database operations  
 In Management Studio, script is now enabled for database commands, including Create, Alter, Delete, Backup, Restore, Attach, Detach. Output is Tabular Model Scripting Language (TMSL) in JSON. See [Tabular Model Scripting Language (TMSL) Reference for XMLA](assetId:///c700d7f8-7e01-4052-a9ad-8200dd4009f2) for more information.  
  
## SSIS Analysis Services Execute DDL Task  
 SSIS Analysis Services Execute DDL Task now also accepts tabular model scripting language commands. Other SSIS-SSAS tasks will be supported in a future CTP to use the new tabular metadata (exceptions will be called out in the release notes).  
  
## SSAS PowerShell cmdlet  
 SSAS PowerShell cmdlet **Invoke-ASCmd** now accepts tabular model scripting language commands. Other SSAS PowerShell cmdlets will be updated in a future CTP to use the new tabular metadata (exceptions will be called out in the release notes).  
See [Analysis Services PowerShell Reference](../../Topics/TopicNameNotContainA/Analysis-Services-PowerShell-Reference.md) for details.  
  
## Translations  
 You can now store translated metadata in a Tabular 1200 model. Metadata in the model includes fields for **Culture**, translated captions, and translated descriptions. To add translations, use the **Model** > **Translations** command in [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)]. See [Translations in Tabular models (Analysis Services)](../../Topics/TopicNameNotContainA/Translations-in-Tabular-models--Analysis-Services-.md) for details.  
  
## Tabular Model Scripting Language (TMSL) supported in SSMS  
 Scripts can be generated in SSMS to easily automate most of the administrative tasks performed in the tool. In CTP 3.2 you can now generate script in SSMS for tabular models at compatibility level 1200. Currently, the following tasks can be scripted: Process at any level, plus CREATE, ALTER, DELETE at the database level. Script is in TMSL (a JSON format).  
  
 Functionally, TMSL is equivalent to the XMLA ASSL extension that provides multidimensional object definitions, except that TMSL uses native descriptors like **model**, **table**, and **relationship** to describe tabular metadata. See [Tabular Model Scripting Language (TMSL) Reference for XMLA](assetId:///c700d7f8-7e01-4052-a9ad-8200dd4009f2) for details about the schema.  
  
 To use this feature, you must [download the version of SSMS that ships concurrently with CTP 3.2](https://msdn.microsoft.com/en-US/library/mt238290.aspx) and connect to a [CTP 3.2 version of an Analysis Services](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) in tabular mode.  
  
 A generated JSON-based script for a tabular model might look like the following:  
  
```  
{  
  "create": {  
    "database": {  
      "name": "AdventureWorksTabular1200",  
      "id": "AdventureWorksTabular1200",  
      "compatibilityLevel": 1200,  
      "readWriteMode": "readWrite",  
      "model": {}  
    }  
  }  
}  
```  
  
 The payload is a JSON document that can be as minimal as the example shown above, or highly embellished with  the full set of object definitions. [Tabular Model Scripting Language (TMSL) Reference for XMLA](assetId:///c700d7f8-7e01-4052-a9ad-8200dd4009f2) describes the syntax.  
  
 At the database level, CREATE, ALTER, and DELETE commands will output TMSL script in the familiar XMLA window.  Other commands, such as Process, can also be scripted in this release. Script support for many other actions is still pending and will be added in subsequent CTPs.  
  
 The following commands are currently available in TMSL script:  
  
|||  
|-|-|  
|**Scriptable commands**|**Description**|  
|create|Adds a database, connection, or partition. The ASSL equivalent is CREATE.|  
|createOrReplace|Updates an existing object definition (database, connection, or partition) by overwriting a previous version. The ASSL equivalent is ALTER with AllowOverwrite set to true and ObjectDefinition to ExpandFull.|  
|delete|Removes an object definition. ASSL equivalent is DELETE.|  
|refresh|Processes the object. ASSL equivalent is PROCESS.|  
  
## Calculated tables in SSDT  
 A *calculated table* is a model-only construction based on a DAX expression or query in SSDT. When deployed in a database, a calculated table is indistinguishable from regular tables.  
  
 There are several uses for calculated tables, including the creation of new tables to expose an existing table in a specific role. The classic example is a Date table that operates in multiple contexts (order date, ship date, and so forth). By creating a calculated table for a given role, you can now activate a table relationship to facilitate queries or data interaction using the calculated table. Another use for calculated tables is to combine parts of existing tables into an entirely new table that exists only in the model.  See [Create a Calculated Table (SSAS Tabular)](../../Topics/TopicNameContainA/Create-a-Calculated-Table--SSAS-Tabular-.md) to learn more.  
  
## DirectQuery  
 This release includes significant enhancements to DirectQuery functionality. Here’s a summary:  
  
-   Row level security (RLS) is now supported for DirectQuery models at compatibility level 1200. Previously, the presence of RLS prevented customers from running a Tabular model in DirectQuery mode.  
  
-   Calculated columns are now supported for DirectQuery models at compatibility level 1200. Previously, the presence of calculated columns prevented customers from running a Tabular model in DirectQuery mode.  
  
-   Performance optimization: redundant join elimination for VertiPaq and DirectQuery.  
  
### New DirectQuery implementation  
 DirectQuery is now available for tabular models that operate at the 1200 compatibility level. With this release, DirectQuery has additional properties and capabilities for tabular 1200 models. Most noteworthy is the extra  control over defining sample datasets used for model design and testing.  See [DirectQuery Mode (SSAS Tabular)](../../Topics/TopicNameNotContainA/DirectQuery-Mode--SSAS-Tabular-.md) to learn more.  
  
> [!NOTE]  
>  Now that DirectQuery is turned on for tabular 1200 models, you might want to upgrade an existing 1103 model to 1200 to use the new features. A direct upgrade isn't supported, but the workaround is easy. Simply open the model in SSDT, set the **DirectQuery Mode** property to **Off**, set **Compatibility Level** to 1200, and then turn DirectQuery back on again.  
  
### New data sources for DirectQuery mode  
 Data sources supported for Tabular 110x models in DirectQuery mode now include Oracle, Teradata and Microsoft Analytics Platform (formerly known as Parallel Data Warehouse).  
  
### Improved query generation for DirectQuery  
 DirectQuery now generates simpler queries that provide better performance.  
  
## Set default for bi-directional cross filters in tabular models in SSDT  
 This release enables bi-directional cross filters by default for tabular models at the 1200 compatibility level in SSDT.  Filters are only auto-generated when the direction can be established with a high degree of certainty. If there is ambiguity in the form of multiple query paths across table relationships, a filter won't be created automatically. See [Bi-directional cross filters for tabular models in SQL Server 2016 Analysis Services](../../Topics/TopicNameNotContainA/Bi-directional-cross-filters-for-tabular-models-in-SQL-Server-2016-Analysis-Services.md) for details.  
  
## Upgrade, roles, and metadata visualization for Tabular 1200 models in SSDT  
  
> [!NOTE]  
>  Be sure to upgrade the SSAS tabular engine if you upgrade to  CTP 3.1 tools. Schema changes to the tabular object model require that both engine and tools are from the same build.  
  
 This release adds new capabilities for tabular model design in the version of [SSDT for Visual Studio 2015 that ships concurrently with CTP 3.1](https://msdn.microsoft.com/en-US/library/mt204009.aspx):  
  
-   **Upgrade a Tabular 1100 or 1103 model to 1200**  
  
     Object metadata is modified to the new JSON format, which will require the JSON editor (see steps below) to see.  
  
     After upgrading, the model can be deployed only on a SQL Server 2016 instance of Analysis Services.  
  
     In Solution Explorer, right-click **Model.bim** > **Properties** > **Compatibility Level**. Change the compatibility level  from 1100 or 1103 to 1200.  
  
-   **Roles in SSDT**  
  
     You can now define roles for Tabular models at the 1200 compatibility level in the Tabular model designer in SSDT.  
  
-   **JSON editor for BIM files**  
  
     The Code View in Visual Studio 2015 now renders the BIM in JSON format for Tabular models at the 1200 compatibility level. The version of Visual Studio determines whether the BIM file is rendered in JSON via the built-in JSON Editor, or as simple text.  
  
     To use the JSON editor, with the ability to expand and collapse sections of the model, you will need the CTP 3.1 version of SQL Server Data Tools plus the Visual Studio 2015 (any edition, including the free Community edition). For all other versions of SSDT or Visual Studio, the BIM file is rendered in JSON as simple text.  
  
    1.  Install  the free [Visual Studio 2015 Community](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) or a higher edition to get the latest JSON editor.  
  
    2.  Install the version of [SSDT for Visual Studio 2015 that ships concurrently with CTP 3.1](https://msdn.microsoft.com/en-US/library/mt204009.aspx) to get the latest updates to the Analysis Services project templates, the Tabular editor, and the Analysis Management Objects (AMO) data provider.  
  
    3.  Start Visual Studio 2015 Community edition and open, upgrade, or create a Tabular model at the 1200 compatibility level.  
  
         By default, Visual Studio 2015 uses 1103 as the default compatibility level so make point of switching to 1200.  
  
    4.  For a workspace server, specify a SQL Server 2016 Analysis Services instance in Tabular mode. You must use a CTP 3.1 version of the server if you are using CTP 3.1 versions of the tools.  
  
    5.  In Solution Explorer, right-click **Model.bim** to select **View Code**.  
  
     At a minimum, an empty model will contain  the following JSON. For more information, see [Tabular Model Scripting Language (TMSL) Reference for XMLA](assetId:///c700d7f8-7e01-4052-a9ad-8200dd4009f2).  
  
    ```  
    {  
      "name": "SemanticModel",  
      "id": "SemanticModel",  
      "compatibilityLevel": 1200,  
      "readWriteMode": "readWrite",  
      "model": {}  
    }  
    ```  
  
    > [!IMPORTANT]  
    >  Avoid editing the JSON directly. Doing so can corrupt the model.  
  
## Partition management for Tabular 1200 models in SSMS  
 You can  now use the version of [SSMS that ships concurrently with CTP 3.1](https://msdn.microsoft.com/en-US/library/mt238290.aspx) to create, process, and merge partitions for Tabular models at the 1200 compatibility level.  
  
## Project templates added for Tabular 1200 models in SSDT  
 With this release, you no longer need two versions of SSDT for building relational and BI projects. [SQL Server Data Tools for Visual Studio 2015](https://msdn.microsoft.com/en-US/library/mt204009.aspx) adds project templates for Analysis Services solutions, including **Analysis Services Tabular Projects** used for building models at the 1200 compatibility level. Other Analysis Services project templates for multidimensional and data mining solutions are also included, but  at the same functional level (1100 or 1103) as in previous releases.  
  
## Improved DAX formula editing  
 Updates to the formula bar help you write formulas with more ease by differentiating functions, fields and measures using syntax coloring, it provides intelligent function and field suggestions and tells you if parts of your DAX expression are wrong using error 'squiggles'. It also allows you to use multiple lines (Alt + Enter) and indentation (Tab). The formula bar now also allows you to write comments as part of your measures, just type “//” and everything after these characters on the same line will be considered a comment.  
  
## Improved SSDT modeling performance for Tabular 1200 models  
 For Tabular 1200 models,  metadata operations in SSDT are much faster. By comparison, on the same hardware, creating a relationship on a model set to the SQL Server 2014 compatibility level (1103) with 23 tables takes 3 seconds, whereas the same relationship on a model created set to compatibility level 1200 takes just under a second.  
  
## Formula fixup  
 With formula fixup on a Tabular 1200 model,  SSDT will automatically update any measures that is referencing a column or table that was renamed.  
  
## Support for Visual Studio configuration manager  
 To support multiple environments, like Test and Pre-production environments, Visual Studio allows developers to create multiple project configurations using the configuration manager. Multidimensional models already leverage this but Tabular models do not. With this release, you can now use configuration manager to deploy to different servers.  
  
## Administration of Tabular 1200 models in SSMS  
 In this release, an  Analysis Services instance in Tabular server mode can run Tabular models at any compatibility level (1100, 1103, 1200). In CTP 3.0 and later, [SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx) is updated to display properties and provide database model administration for Tabular models at the 1200 compatibility level.  
  
## Analysis Services Management Objects (AMO) updates  
 In this release, [Analysis Services Management Objects (AMO)](assetId:///dcffdfde-0b83-4df1-8140-7f6ad1fc71fd) has been re-factored to include a second assembly, Microsoft.AnalysisServices.Core.dll. The new assembly separates out common classes like Server, Database, and Role that have broad application in Analysis Services, irrespective of server mode.  
  
 Previously, these classes were part of the original Microsoft.AnalysisServices assembly. Moving them to a new assembly paves the way for future extensions to AMO, with clear division between generic and context-specific APIs.  
  
 Existing applications are unaffected by the new assemblies. However, should you choose to rebuild applications using the new AMO assembly for any reason, be sure to add a reference to Microsoft.AnalysisServices.Core.  
  
 Similarly, PowerShell scripts that load and call into AMO must now load Microsoft.AnalysisServices.Core.dll. Please update any scripts prior to pointing them to a CTP 3.0 version of SQL Server 2016 Preview Analysis Services.  
  
> [!NOTE]  
>  In CTP 3.0, AMO cannot be used to author new tabular 1200 models. In a subsequent CTP, AMO will be extended with a tabular object model that can be used for that purpose.  
  
## DBCC for Analysis Services  
 Database Consistency Checker (DBCC) runs internally to detect potential data corruption issues on database load, but can also be run on demand if you suspect problems in your data or model. DBCC runs different checks depending on whether the model is tabular or multidimensional. See [Database Consistency Checker (DBCC) for Analysis Services tabular and multidimensional databases](../../Topics/TopicNameNotContainA/Database-Consistency-Checker--DBCC--for-Analysis-Services-tabular-and-multidimensional-databases.md) for details.  
  
## Extended Events updates  
 This release adds a graphical user interface to [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to configure and manage [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] Extended Events. You can set up live data streams to monitor server activity in real time, keep session data loaded in memory for faster analysis, or save data streams to a file for offline analysis. For more information, see [Monitor Analysis Services with SQL Server Extended Events](../../Topics/TopicNameNotContainA/Monitor-Analysis-Services-with-SQL-Server-Extended-Events.md) and [Using extended events with Analysis Services (Guy in a Cube blog post and video)](http://blogs.msdn.com/b/analysisservices/archive/2015/09/22/using-extended-events-with-sql-server-analysis-services-2016-cpt-2-3.aspx).  
  
## DAX  
  
### New behaviors for DAX variables  
 SQL Server 2016 CTP 2.3 includes new includes support for variables in DAX. Variables can now store the result of an expression as a named variable, which can then be passed as an argument to other measure expressions. Once resultant values have been calculated for a variable expression, those values do not change, even if the variable is referenced in another expression. For more information, see [VAR Function](https://msdn.microsoft.com/en-us/library/mt243785.aspx).  
  
### New DAX functions  
 The Data Analysis Expressions formula language introduces over fifty new functions to support faster calculations and enhanced visualizations in Power BI. To learn more, see [New DAX Functions](https://msdn.microsoft.com/en-us/library/mt704075.aspx).  
  
### Saving incomplete measures  
 You can now save incomplete DAX measures directly in a Tabular 1200 model   project and pick it up again when you are ready to continue.  
  
## Parallel processing for multiple table partitions in Tabular models  
 This release includes new parallel processing functionality for tables with two or more partitions, increasing processing performance. There are no configuration settings for this feature. For more information about configuring partitions and processing tables, see [Tabular Model Partitions (SSAS Tabular)](../../Topics/TopicNameNotContainA/Tabular-Model-Partitions--SSAS-Tabular-.md).  
  
## Add computer accounts as Administrators in SSMS  
 [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] administrators can now use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to configure computer accounts to be members of the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] administrators group. In the **Select Users or Groups** dialog, set the **Locations** for the computers domain and then add the **Computers** object type. For more information, see [Grant server admin rights to an  Analysis Services instance](../../Topics/TopicNameNotContainA/Grant-server-admin-rights-to-an--Analysis-Services-instance.md).  
  
## New elements in MS-CSDLBI 2.0 schema  
 The following elements have been added to the **TProperty** complex type defined in the [MS-CSDLBI] 2.0 schema:  
  
|Element|Definition|  
|-------------|----------------|  
|DefaultValue|A property that specifies the value used when evaluating the query. The DefaultValue property is optional, but it is automatically selected if the values from the member cannot be aggregated.|  
|Statistics|A set of statistics from the underlying data that is associated with the column. These statistics are defined by the TPropertyStatistics complex type and are provided only if they are not computationally expensive to generate, as described in section 2.1.13.5 of the Conceptual Schema Definition File Format with Business Intelligence Annotations document.|  
  
## See Also  
 [What's New in SQL Server 2016](../../Topics/TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md)   
 [What's New in Database Engine](../../Topics/TopicNameNotContainA/What-s-New-in-Database-Engine.md)   
 [What's New in Reporting Services (SSRS)](../../Topics/TopicNameNotContainA/What-s-New-in-Reporting-Services--SSRS-.md)