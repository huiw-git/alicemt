---
title: Map Query Parameters to Variables in a Data Flow Component
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
---
# Map Query Parameters to Variables in a Data Flow Component
  When you configure the OLE DB source to use parameterized queries, you can map the parameters to variables.  
  
 The OLE DB source uses parameterized queries to filter data when the source connects to a data source.  
  
### To map a query parameter to a variable  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it.  
  
3.  Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.  
  
4.  Right\-click the OLE DB source, and then click **Edit**.  
  
5.  In the **OLE DB Source Editor**, select an OLE DB connection manager to use to connect to the data source, or click **New** to create a new OLE DB connection manager.  
  
6.  Select the **SQL command** option for data access mode, and then type a parameterized query in the **SQL command text** pane.  
  
7.  Click **Parameters**.  
  
8.  In the **Set Query Parameters** dialog box, map each parameter in the **Parameters** list to a variable in the **Variables** list, or create a new variable by clicking **\<New variable\>**. Click **OK**.  
  
    > [!NOTE]  
    >  Only system variables and user\-defined variables that are in the scope of the package, a parent container such as a Foreach Loop, or the Data Flow task that contains the data flow component are available for mapping. The variable must have a data type that is compatible with the column in the WHERE clause to which the parameter is assigned.  
  
9. You can click **Preview** to view up to 200 rows of the data that the query returns.  
  
10. To save the updated package, click **Save Selected Items** on the **File** menu.  
  
## See Also  
 [OLE DB Source](../../Topics\TopicNameNotContainA/OLE-DB-Source.md)   
 [Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md)  
  
  