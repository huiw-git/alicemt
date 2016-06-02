---
title: Create a Data Mining Query by Using XMLA
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
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
---
# Create a Data Mining Query by Using XMLA
  You can create a variety of queries against data mining objects by using AMO, DMX, or XML\/A.  
  
 XML is used for communication between the Analysis Services server and all clients. Therefore, although it is generally much easier to create content queries by using DMX, you can write queries by using the DISCOVER and COMMAND statements in XML\/A, either by using a client that supports the SOAP protocol, or by creating an XML\/A query in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 This topic explains how to use the XML\/A templates that are available in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to create a model content query against a mining model stored on the current server.  
  
## Querying Data Mining Schema Rowsets by Using XML\/A  
  
#### To open an XML\/A template  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], on the **View** menu, click **Template Explorer**.  
  
2.  Click the cube icon to open the list of Analysis Services templates.  
  
3.  In the list of template categories, expand **XMLA**, expand **Schema Rowsets**, and double\-click **Discover Schema Rowsets** to open the template in the appropriate code editor.  
  
4.  In the **Connect to Analysis Services** dialog box, complete the connection information and then click **Connect**. A new query editor window opens, populated with the **Discover Schema Rowsets** template.  
  
#### To discover column names from the MINING MODEL CONTENT schema rowset  
  
1.  With the **Discover Schema Rowsets** template open, click **Execute**.  
  
     A list of schema rowsets is returned in the **Results** pane that contains the rowset names and rowset columns for all rowsets available on the current instance.  
  
2.  In the **Query** pane, place the cursor after **\<Restriction List\>** and press ENTER to add a new line.  
  
3.  Place the cursor on the blank line and type **\<SchemaName\>DMSCHEMA\_MINING\_MODEL\_CONTENT\<\/SchemaName\>**  
  
     The complete section for restrictions should appear as follows:  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  Click **Execute**.  
  
     The **Results** pane shows a list of column names for the specified schema rowset.  
  
#### To create a content query using the MINING MODEL CONTENT schema rowset  
  
1.  In the **Discover Schema Rowsets** template, change the request type by replacing the text inside the request type tags.  
  
     Replace this line:  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     with the following line:  
  
     **\<RequestType\>DMSCHEMA\_MINING\_MODEL\_CONTENT\<\/RequestType\>**  
  
2.  Change the restriction list to specify a mining model by name, by adding a new condition to the restriction lists.  
  
3.  In the template, place the cursor after `<Restriction List>` and press ENTER to add a new line.  
  
4.  Place the cursor on the blank line and type **\<MODEL\_NAME\>My model name\<\/MODEL\_NAME\>**  
  
     The complete section for restrictions should appear as follows:  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  Click **Execute**.  
  
     The Results pane displays the schema definition, together with the values for the specified model.  
  
## See Also  
 [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Data Mining Schema Rowsets](../Topic/Data%20Mining%20Schema%20Rowsets.md)  
  
  