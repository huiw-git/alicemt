---
title: Deployment of Data Mining Solutions
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
ms.assetid: d83effc7-437d-42e9-8ac3-b65f79e27043
---
# Deployment of Data Mining Solutions
  The last step in the data mining process is to deploy the models to a production environment. Deployment is important because it makes the models available to users so that you can perform any of the following tasks:  
  
-   Use the models to create predictions and make business decisions. For information about the tools you can use to create queries, see [Data Mining Query Tools](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tools.md).  
  
-   Embed data mining functionality directly into an application. You can include Analysis Management Objects \(AMO\) or an assembly that contains a set of objects that your application can use to create, alter, process, and delete mining structures and mining models.  
  
-   Create reports that let users request predictions, view trends, or compare models.  
  
 This section provides detailed information about deployment options.  
  
 [Requirements for Deployment of Data Mining Solutions](#bkmk_Reqs)  
  
 [Deploying a Relational Solution](#bkmk_RelationalSltn)  
  
 [Deploying a Multidimensional Solution](#bkmk_MDSltn)  
  
 [Related Resources](#bkmk_Resources)  
  
## In This Section  
 [Deploy a Data Mining Solution to Previous Versions of SQL Server](../../Topics\TopicNameContainA/Deploy-a-Data-Mining-Solution-to-Previous-Versions-of-SQL-Server.md)  
  
 [Export and Import Data Mining Objects](../../Topics\TopicNameNotContainA/Export-and-Import-Data-Mining-Objects.md)  
  
##  <a name="bkmk_Reqs"></a> Requirements for Deployment of Data Mining Solutions  
 The instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data.  
  
 Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.  
  
 When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance, in a database with the same name as the solution file.  
  
###  <a name="bkmk_RelationalSltn"></a> Deploying a Relational Solution  
 When you deploy a relational data mining solution, the required data mining objects are created within a new [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, and the objects are processed by default. You can change processing options by using the configuration property, **Processing Option**. For more information, see [Configure Analysis Services Project Properties &#40;SSDT&#41;](../Topic/Configure%20Analysis%20Services%20Project%20Properties%20\(SSDT\).md).  
  
 By default, only incremental changes are deployed each time. In other words, you can modify a mining model, and when you re\-deploy the project, only that mining model would be updated. However, if you have multiple clients editing the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, this can lead to errors. To change the default deployment mode so that the entire database is refreshed when you deploy the solution, change the **Deployment Mode** property  
  
 In a relational data mining solution, the only objects that must be deployed are the data source definition, any data source views that were used, the mining structures, and all dependent mining models.  
  
###  <a name="bkmk_MDSltn"></a> Deploying a Multidimensional Solution  
 When you deploy a multidimensional data mining solution, this solution creates your data mining objects within the same database as the source cube.  
  
 When you process the mining structure or mining model, you must process the source cube as well. For this reason, deploying a solution that uses OLAP mining models can take longer than relational data mining solutions.  
  
 Typically data mining objects also use the same data sources and data source views that are used for the cube. However, you can add data sources and data source views that are targeted specifically to data mining. For example, typically a cube would not contain data about prospective clients, or external data not used in the multidimensional objects.  
  
##  <a name="bkmk_Resources"></a> Related Resources  
 [Moving Data Mining Objects](../../Topics\TopicNameNotContainA/Moving-Data-Mining-Objects.md)  
  
 If your model is based on relational data only, exporting and importing objects using DMX is the easiest way to move models.  
  
 [Move an Analysis Services Database](../../Topics\TopicNameNotContainA/Move-an-Analysis-Services-Database.md)  
  
 When models use a cube as a data source, refer to this topic for more information about how to move models and their supporting cube data.  
  
 [Deploy Analysis Services Projects &#40;SSDT&#41;](../Topic/Deploy%20Analysis%20Services%20Projects%20\(SSDT\).md)  
  
 Provides general information about deployment of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] projects, and describes the properties that you can set as part of the project configuration.  
  
## See Also  
 [Processing a multidimensional model &#40;Analysis Services&#41;](../Topic/Processing%20a%20multidimensional%20model%20\(Analysis%20Services\).md)   
 [Data Mining Query Tools](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tools.md)   
 [Processing Requirements and Considerations &#40;Data Mining&#41;](../Topic/Processing%20Requirements%20and%20Considerations%20\(Data%20Mining\).md)  
  
  