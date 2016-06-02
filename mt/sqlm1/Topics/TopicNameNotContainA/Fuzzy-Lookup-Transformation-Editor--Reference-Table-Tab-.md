---
title: Fuzzy Lookup Transformation Editor (Reference Table Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
---
# Fuzzy Lookup Transformation Editor (Reference Table Tab)
  Use the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor** dialog box to specify the source table and the index to use for the lookup. The reference data source must be a table in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database.  
  
> [!NOTE]  
>  The Fuzzy Lookup transformation creates a working copy of the reference table. The indexes described below are created on this working table by using a special table, not an ordinary [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] index. The transformation does not modify the existing source tables unless you select **Maintain stored index**. In this case, it creates a trigger on the reference table that updates the working table and the lookup index table based on changes to the reference table.  
  
> [!NOTE]  
>  The **Exhaustive** and the **MaxMemoryUsage** properties of the Fuzzy Lookup transformation are not available in the **Fuzzy Lookup Transformation Editor**, but can be set by using the **Advanced Editor**. In addition, a value greater than 100 for **MaxOutputMatchesPerInput** can be specified only in the **Advanced Editor**. For more information on these properties, see the Fuzzy Lookup Transformation section of [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md).  
  
 To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](../../Topics\TopicNameNotContainA/Fuzzy-Lookup-Transformation.md).  
  
## Options  
 **OLE DB connection manager**  
 Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.  
  
 **New**  
 Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.  
  
 **Generate new index**  
 Specify that the transformation should create a new index to use for the lookup.  
  
 **Reference table name**  
 Select the existing table to use as the reference \(lookup\) table.  
  
 **Store new index**  
 Select this option if you want to save the new lookup index.  
  
 **New index name**  
 If you have chosen to save the new lookup index, type a descriptive name for the index.  
  
 **Maintain stored index**  
 If you have chosen to save the new lookup index, specify whether you also want [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to maintain the index.  
  
> [!NOTE]  
>  When you select **Maintain stored index** on the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor**, the transformation uses managed stored procedures to maintain the index. These managed stored procedures use the common language runtime \(CLR\) integration feature in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. By default, CLR integration in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is not enabled. To use the **Maintain stored index** functionality, you must enable CLR integration. For more information, see [Enabling CLR Integration](../Topic/Enabling%20CLR%20Integration.md).  
>   
>  Because the **Maintain stored index** option requires CLR integration, this feature works only when you select a reference table on an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] where CLR integration is enabled.  
  
 **Use existing index**  
 Specify that the transformation should use an existing index for the lookup.  
  
 **Name of an existing index**  
 Select a previously created lookup index from the list.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../Topic/Fuzzy%20Lookup%20Transformation%20Editor%20\(Columns%20Tab\).md)   
 [Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;](../Topic/Fuzzy%20Lookup%20Transformation%20Editor%20\(Advanced%20Tab\).md)  
  
  