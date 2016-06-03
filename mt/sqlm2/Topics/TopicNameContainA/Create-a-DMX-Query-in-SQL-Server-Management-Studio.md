---
title: Create a DMX Query in SQL Server Management Studio
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
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
---
# Create a DMX Query in SQL Server Management Studio
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a set of features to help you create prediction queries, content queries, and data definition queries against mining models and mining structures.  
  
-   The graphical Prediction Query Builder is available in both [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] and [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], to simplify the process of writing prediction queries and mapping data sets to a model.  
  
-   The query templates provided in the Template Explorer jump\-start the creation of many kinds of DMX queries, including many types of prediction queries. Templates are provided for content queries, queries used nested data sets, queries that return cases from the mining structure, and even data definition queries.  
  
-   The Metadata Explorer in the MDX and DMX query panes provides a list of available models and structures that you can drag and drop into the query builder, as well as a list of DMX functions. This feature makes it easy to get object names right, without typing.  
  
 This topic describes how to build a DMX query by using the Metadata Explorer and the DMX query editor.  
  
##  <a name="BKMK_Templates"></a> DMX Query Templates  
 Templates for creating basic DMX queries are available in Template Explorer. The **DMX** folder contains data mining templates, which are divided into these categories:  
  
-   **Model Content**  
  
-   **Model Management**  
  
-   **Prediction Queries**  
  
-   **Structure Content**  
  
 You can also create custom templates, for queries or commands that you run frequently.  
  
## XMLA Query Templates  
 [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] also provides templates for XMLA queries.  
  
 There is some overlap between the types of queries that you can perform by using XMLA and DMX. For example, you can create some model content queries by using either DMX or the data mining schema rowsets, but the schema rowsets sometimes contain information that is not exposed in DMX content queries.  
  
 There are also some key differences in the way that operations are handled in DMX and in XMLA. For example, you can use XMLA to perform administrative operations such as backup of an entire [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, but if you want to back up a single mining model, DMX provides a simple command, [EXPORT &#40;DMX&#41;](../Topic/EXPORT%20\(DMX\).md), that is better suited to that purpose.  
  
##  <a name="BKMK_Building_Queries"></a> Build and Run a DMX Query  
  
#### Open a new DMX Query window  
  
1.  Click **New Query** in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then select **New Analysis Server DMX Query**.  
  
2.  When the **Connect to Server** dialog box appears, select the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] that contains the mining models you want to work with.  
  
#### Open Template Explorer  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], on the **View** menu, select **Template Explorer**.  
  
2.  Click **Analysis Server** to see a tree view of the templates that apply to [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].  
  
#### Apply a template to build a query  
  
-   Right\-click the appropriate query type and select **Open**.  
  
-   Or, drag the template into the query editor.  
  
-   You can also fill in the parameters for the query by using the option, **Specify Values for Parameters**, from the **Query** menu.  
  
 For examples of how to create specific types of queries from templates, see the following topics:  
  
 [Create a Singleton Prediction Query from a Template](../../Topics\TopicNameContainA/Create-a-Singleton-Prediction-Query-from-a-Template.md)  
  
 [Create a Content Query on a Mining Model](../../Topics\TopicNameContainA/Create-a-Content-Query-on-a-Mining-Model.md)  
  
## See Also  
 [Data Mining Query Tools](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tools.md)   
 [Data Mining Extensions &#40;DMX&#41; Reference](../Topic/Data%20Mining%20Extensions%20\(DMX\)%20Reference.md)  
  
  