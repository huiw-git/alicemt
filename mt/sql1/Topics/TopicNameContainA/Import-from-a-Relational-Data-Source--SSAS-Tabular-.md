---
title: "Import from a Relational Data Source (SSAS Tabular)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 16
manager: mblythe
---
# Import from a Relational Data Source (SSAS Tabular)
You can import data from a variety of relational databases by using the Table Import Wizard. The wizard is available in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], on the **Model** menu. To connect to a data source, you must have the appropriate provider installed on your computer. For more information about supported data sources and providers, see [Data Sources Supported (SSAS Tabular)](../../Topics/TopicNameNotContainA/Data-Sources-Supported--SSAS-Tabular-.md).  
  
 The Table Import Wizard supports importing data from the following data sources:  
  
 **Relational Databases**  
  
-   Microsoft SQL Server database  
  
-   Microsoft SQL Azure  
  
-   Microsoft Access database  
  
-   Microsoft SQL Server Parallel Data Warehouse  
  
-   Oracle  
  
-   Teradata  
  
-   Sybase  
  
-   Informix  
  
-   IBM DB2  
  
-   OLE DB/ODBC  
  
 **Multidimensional Sources**  
  
-   Microsoft SQL Server Analysis Services cube  
  
 The Table Import Wizard does not support importing data from a [!INCLUDE[ssGemini](../../Topics/TopicNameContainA/tokens/ssGemini_md.md)] Workbook as a data source.  
  
### To import data from a database  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], click the **Model** menu, and then click **Import from Data Source**.  
  
2.  On the **Connect to a Data Source** page, select the type of database to connect to, and then click **Next**.  
  
3.  Follow the steps in the Table Import Wizard. On subsequent pages, you will be able to select specific tables and views or apply filters by using the **Select Tables and Views** page or by creating a SQL query on **Specify a SQL Query** page.  
  
## See Also  
 [Import Data (SSAS Tabular)](../../Topics/TopicNameNotContainA/Import-Data--SSAS-Tabular-.md)   
 [Data Sources Supported (SSAS Tabular)](../../Topics/TopicNameNotContainA/Data-Sources-Supported--SSAS-Tabular-.md)