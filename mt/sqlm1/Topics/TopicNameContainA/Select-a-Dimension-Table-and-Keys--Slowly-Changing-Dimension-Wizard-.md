---
title: Select a Dimension Table and Keys (Slowly Changing Dimension Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
---
# Select a Dimension Table and Keys (Slowly Changing Dimension Wizard)
  Use the **Select a Dimension Table and Keys** page to select a dimension table to load. Map columns from the data flow to the columns that will be loaded.  
  
 To learn more about this wizard, see [Slowly Changing Dimension Transformation](../../Topics\TopicNameNotContainA/Slowly-Changing-Dimension-Transformation.md).  
  
## Options  
 **Connection manager**  
 Select an existing OLE DB connection manager from the list, or click **New** to create an OLE DB connection manager.  
  
> [!NOTE]  
>  The Slowly Changing Dimension Wizard only supports OLE DB connection managers, and only supports connections to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 **New**  
 Use the **Configure OLE DB Connection Manager** dialog box to select an existing connection manager, or click **New** to create a new OLE DB connection.  
  
 **Table or View**  
 Select a table or view from the list.  
  
 **Input Columns**  
 Select from the list of input columns for which you may specify mapping.  
  
 **Dimension Columns**  
 View all available dimension columns.  
  
 **Key Type**  
 Select one of the dimension columns to be the business key. You must have one business key.  
  
## See Also  
 [Configure Outputs Using the Slowly Changing Dimension Wizard](../../Topics\TopicNameNotContainA/Configure-Outputs-Using-the-Slowly-Changing-Dimension-Wizard.md)  
  
  