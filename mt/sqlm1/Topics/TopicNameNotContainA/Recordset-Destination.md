---
title: Recordset Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
---
# Recordset Destination
  The Recordset destination creates and populates an in\-memory ADO recordset. The shape of the recordset is defined by the input to the Recordset destination at design time.  
  
## Configuration of the Recordset Destination  
 You configure the Recordset destination by specifying the variable that stores the ADO recordset.  
  
 At run time, an ADO recordset is written to the variable of type, Object, that is specified in the VariableName property of the Recordset destination. The variable then makes the Recordset available outside the data flow, where it can be used by scripts and other package elements.  
  
 This source has one input. It does not support an error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Recordset Destination Custom Properties](../../Topics\TopicNameNotContainA/Recordset-Destination-Custom-Properties.md)  
  
 For more information about how to set the properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## Related Tasks  
 [Use a Recordset Destination](../../Topics\TopicNameContainA/Use-a-Recordset-Destination.md)  
  
  