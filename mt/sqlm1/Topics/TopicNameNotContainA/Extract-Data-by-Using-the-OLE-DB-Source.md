---
title: Extract Data by Using the OLE DB Source
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
---
# Extract Data by Using the OLE DB Source
  To add and configure an OLE DB source, the package must already include at least one Data Flow task.  
  
### To extract data using an OLE DB Source  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it.  
  
3.  Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.  
  
4.  Double\-click the OLE DB source.  
  
5.  In the **OLE DB Source Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager. For more information, see [OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md).  
  
6.  Select the data access method:  
  
    -   **Table or view** Select a table or view in the database to which the OLE DB connection manager connects.  
  
    -   **Table name or view name variable** Select the user\-defined variable that contains the name of a table or view in the database to which the OLE DB connection manager connects.  
  
    -   **SQL command** Type an SQL command or click **Build Query** to write an SQL command using the **Query Builder**.  
  
        > [!NOTE]  
        >  The command can include parameters. For more information, see [Map Query Parameters to Variables in a Data Flow Component](../../Topics\TopicNameContainA/Map-Query-Parameters-to-Variables-in-a-Data-Flow-Component.md).  
  
    -   **SQL command from variable** Select the user\-defined variable that contains the SQL command.  
  
        > [!NOTE]  
        >  The variables must be defined in the scope of the same Data Flow task that contains the OLE DB source, or in the scope of the same package; additionally, the variable must have a string data type.  
  
7.  To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.  
  
8.  Optionally, update the names of output columns by editing values in the **Output Column** list.  
  
9. To configure the error output, click **Error Output**. For more information, see [Configure an Error Output in a Data Flow Component](../../Topics\TopicNameContainA/Configure-an-Error-Output-in-a-Data-Flow-Component.md).  
  
10. You can click **Preview** to view up to 200 rows of the data extracted by the OLE DB source.  
  
11. Click **OK**.  
  
12. To save the updated package, click **Save Selected Items** on the **File** menu.  
  
## See Also  
 [OLE DB Source](../../Topics\TopicNameNotContainA/OLE-DB-Source.md)   
 [Integration Services Transformations](../../Topics\TopicNameNotContainA/Integration-Services-Transformations.md)   
 [Integration Services Paths](../../Topics\TopicNameNotContainA/Integration-Services-Paths.md)   
 [Data Flow Task](../../Topics\TopicNameNotContainA/Data-Flow-Task.md)  
  
  