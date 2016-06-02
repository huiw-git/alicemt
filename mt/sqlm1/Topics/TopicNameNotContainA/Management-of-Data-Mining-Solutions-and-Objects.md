---
title: Management of Data Mining Solutions and Objects
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
---
# Management of Data Mining Solutions and Objects
  [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] provides client tools that you can use to manage existing mining structures and mining models. This section describes the management operations that you can perform using each environment.  
  
 In addition to these tools, you can manage data mining objects programmatically, by using AMO, or use other clients that connect to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, such as the Data Mining Add\-ins for [!INCLUDE[ofprexcel](../../Token\Other/ofprexcel_md.md)] 2007.  
  
## In this Section  
 [Moving Data Mining Objects](../../Topics\TopicNameNotContainA/Moving-Data-Mining-Objects.md)  
  
 [Processing Requirements and Considerations &#40;Data Mining&#41;](../Topic/Processing%20Requirements%20and%20Considerations%20\(Data%20Mining\).md)  
  
 [Using SQL Server Profiler to Monitor Data Mining &#40;Analysis Services - Data Mining&#41;](../Topic/Using%20SQL%20Server%20Profiler%20to%20Monitor%20Data%20Mining%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
## Location of Data Mining Objects  
 Mining structures and models that have been processed are stored in an instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].  
  
 If you create a connection to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database in **Immediate** mode when developing your data mining objects, any objects that you create are immediately added to the server as you work. However, if you design data mining objects in **Offline** mode, which is the default when you work in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], the mining objects that you create are only metadata containers until you deploy them to an instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. Therefore, any time that you make a change to an object, you must redeploy the object to the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] server. For more information about data mining architecture, see [Physical Architecture &#40;Analysis Services - Data Mining&#41;](../Topic/Physical%20Architecture%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
> [!NOTE]  
>  Some clients, such as the Data Mining Add\-ins for [!INCLUDE[ofprexcel](../../Token\Other/ofprexcel_md.md)] 2007, also let you create session mining models and mining structures, which use a connection to an instance but store the mining structure and models on the server only for the duration of the session. You can still manage these models through the client, the same as you would structures and models stored in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, but the objects are not persisted after you disconnect from the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].  
  
## Managing Data Mining Objects in SQL Server Data Tools  
 [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] offers features that make it easy to create, browse, and edit data mining objects.  
  
 The following links provide information on how you can modify data mining objects by using [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]:  
  
-   [Edit the Data Source View used for a Mining Structure](../../Topics\TopicNameContainA/Edit-the-Data-Source-View-used-for-a-Mining-Structure.md)  
  
-   [Change the Properties of a Mining Structure](../../Topics\TopicNameContainA/Change-the-Properties-of-a-Mining-Structure.md)  
  
-   [Change the Properties of a Mining Model](../../Topics\TopicNameContainA/Change-the-Properties-of-a-Mining-Model.md)  
  
-   [View or Change Modeling Flags &#40;Data Mining&#41;](../Topic/View%20or%20Change%20Modeling%20Flags%20\(Data%20Mining\).md)  
  
-   [View or Change Algorithm Parameters](../../Topics\TopicNameNotContainA/View-or-Change-Algorithm-Parameters.md)  
  
 Typically you will use [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] as a tool for developing new projects and adding to existing projects, and then manage projects and objects that have been deployed by using tools such as [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 However, you can directly modify objects that are already deployed to an instance of ssASnoversion by using the **Immediate** option and connecting to the server in Online mode. For more information, see [Connect in Online Mode to an Analysis Services Database](../../Topics\TopicNameNotContainA/Connect-in-Online-Mode-to-an-Analysis-Services-Database.md).  
  
> [!WARNING]  
>  All changes to a mining structure or mining model, including changes to metadata such as a name or description, require that the structure or model be reprocessed.  
  
 If you do not have the solution file that was used to create the data mining project or objects, you can import the existing project from the server using the Analysis Services Import wizard, make modifications to the objects, and then redeploy using the **Incremental** option. For more information, see [Import a Data Mining Project using the Analysis Services Import Wizard](../../Topics\TopicNameContainA/Import-a-Data-Mining-Project-using-the-Analysis-Services-Import-Wizard.md).  
  
## Managing Data Mining Objects in SQL Server Management Studio  
 In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], you can script, process, or delete mining structures and mining models. You can view only a limited set of properties by using Object Explorer; however, you can view additional metadata about mining models by opening a **DMX Query** window and selecting a mining structure.  
  
-   [Create a DMX Query in SQL Server Management Studio](../../Topics\TopicNameContainA/Create-a-DMX-Query-in-SQL-Server-Management-Studio.md)  
  
## Managing Data Mining Objects Programmatically  
 You can create, alter, process, and delete data mining objects by using the following programming languages. Each language is designed for different tasks and as a result, there might be restrictions on the type of operations that you can perform. For example, some properties of data mining objects cannot be changed by using Data Mining Extensions \(DMX\); you must use XMLA or AMO.  
  
### Analysis Management Objects \(AMO\)  
 Analysis Management Objects \(AMO\) is an object model built on top of XMLA that gives you full control over data mining objects. By using AMO, you can create, deploy, and monitor mining structures and mining models  
  
-   [AMO Concepts and Object Model](../Topic/AMO%20Concepts%20and%20Object%20Model.md)  
  
-   [Microsoft.AnalysisServices](assetId:///N:Microsoft.AnalysisServices)  
  
 **Restrictions:** None.  
  
### Data Mining Extensions \(DMX\)  
 Data Mining Extensions \(DMX\) can be used with other command interfaces such as [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] or ADOMD.Net to create, delete, and query mining structures and mining models.  
  
-   [Data Mining Extensions &#40;DMX&#41; Data Definition Statements](../Topic/Data%20Mining%20Extensions%20\(DMX\)%20Data%20Definition%20Statements.md)  
  
 **Restrictions:** Some properties cannot be changed by using DMX.  
  
### XML for Analysis \(XMLA\)  
 XML for Analysis \(XMLA\) is the data definition language for all of Analysis Services. XMLA gives you control over most data mining objects and server operations. All management operations between the client and the server can be performed by using XMLA. For convenience, you can use the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Scripting Language \(ASSL\) to wrap the XML.  
  
 **Restrictions:** [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] generates some XMLA statements that are supported for internal use only, and cannot be used in XML DDL scripts.  
  
## See Also  
 [Analysis Services Developer Documentation](../Topic/Analysis%20Services%20Developer%20Documentation.md)  
  
  