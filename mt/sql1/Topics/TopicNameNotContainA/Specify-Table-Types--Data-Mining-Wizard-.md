---
title: "Specify Table Types (Data Mining Wizard)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Specify Table Types (Data Mining Wizard)
Use the **Specify Table Types** page to identify the tables to use to define the mining structure. If a table is not selected, it will not be used to define the mining structure.  
  
> [!NOTE]  
>  You can add tables later from the **Mining Structure** tab in **Data Mining Designer**.  
  
 **For More Information:** [Nested Tables (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Nested-Tables--Analysis-Services---Data-Mining-.md), [Data Mining Wizard (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard--Analysis-Services---Data-Mining-.md), [Create a Relational Mining Structure](../../Topics/TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Tables**  
 Displays the tables in the data source view that you selected on the **Select Data Source View** page of the wizard.  
  
 **Case**  
 Select one table to use as the case table.  
  
 **Nested**  
 Select the tables to use as nested tables.  
  
> [!NOTE]  
>  These tables must have a many-to-one relationship with the case table, not a one-to-many relationship. You must specify this relationship in the data source view before you can select the table as nested.  
  
## See Also  
 [Data Mining Wizard F1 Help (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Wizard-F1-Help--Analysis-Services---Data-Mining-.md)   
 [Select Data Source View (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Select-Data-Source-View--Data-Mining-Wizard-.md)   
 [Specify the Training Data (Data Mining Wizard)](../../Topics/TopicNameNotContainA/Specify-the-Training-Data--Data-Mining-Wizard-.md)