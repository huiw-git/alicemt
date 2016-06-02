---
title: Fixed and Changing Attribute Options (Slowly Changing Dimension Wizard
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
---
# Fixed and Changing Attribute Options (Slowly Changing Dimension Wizard
  Use the **Fixed and Changing Attribute Options** dialog box to specify how to respond to changes in fixed and changing attributes.  
  
 To learn more about this wizard, see [Slowly Changing Dimension Transformation](../../Topics\TopicNameNotContainA/Slowly-Changing-Dimension-Transformation.md).  
  
## Options  
 **Fixed attributes**  
 For fixed attributes, indicate whether the task should fail if a change is detected in a fixed attribute.  
  
 **Changing attributes**  
 For changing attributes, indicate whether the task should change outdated or expired records, in addition to current records, when a change is detected in a changing attribute. An expired record is a record that has been replaced with a newer record by a change in a historical attribute \(a Type 2 change\). Selecting this option may impose additional processing requirements on a multidimensional object constructed on the relational data warehouse.  
  
## See Also  
 [Configure Outputs Using the Slowly Changing Dimension Wizard](../../Topics\TopicNameNotContainA/Configure-Outputs-Using-the-Slowly-Changing-Dimension-Wizard.md)  
  
  