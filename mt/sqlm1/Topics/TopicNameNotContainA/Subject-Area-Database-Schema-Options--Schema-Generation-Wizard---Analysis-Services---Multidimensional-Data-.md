---
title: Subject Area Database Schema Options (Schema Generation Wizard) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
---
# Subject Area Database Schema Options (Schema Generation Wizard) (Analysis Services - Multidimensional Data)
  Use the **Subject Area Database Schema Options** page to control how the schema is generated, as well as to define how data is preserved.  
  
## Options  
 **Owning schema**  
 Specifies the name of the schema within the new subject area database.  
  
 **Create primary keys on dimension tables**  
 Creates primary keys on the dimension tables in the generated schema. No index is generated if you do not select this option.  
  
> [!NOTE]  
>  If you do not select this option, referential integrity is enforced.  
  
 **Create indexes**  
 Creates indexes on foreign key columns in the generated schema.  
  
 **Enforce referential integrity**  
 Enforces referential integrity within the generated schema. If you do not select this option, relationships are created but not enforced.  
  
 **Preserve data on regeneration**  
 Retains data in the subject area database when the wizard finishes. If you do not select this option, all the data in the subject area database may be erased without warning.  
  
 **Populate time table\(s\)**  
 Specifies how the wizard populates the time tables. The following table describes the possible values for this option.  
  
> [!NOTE]  
>  This option is enabled only if Schema Generation Wizard is called from an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, using [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] in project mode.  
  
|Value|Description|  
|-----------|-----------------|  
|Populate|The subject area time tables are populated.|  
|Do not populate|The subject area time tables are not populated.|  
|Populate only if empty|The subject area time tables are populated only if they are empty.|  
  
## See Also  
 [Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Schema%20Generation%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  