---
title: "Translation support in Analysis Services"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 018471e0-3c82-49ec-aa16-467fb58a6d5f
caps.latest.revision: 35
manager: mblythe
---
# Translation support in Analysis Services
In an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] data models, you can embed multiple translations of a caption or description to provide culture-specific strings based on the LCID. For multidimensional models, translations can be added for the database name, cube objects, and database dimension objects. For tabular models, you can translate table and column captions and descriptions.  
  
 Defining a translation creates the metadata and translated caption inside the model, but to render localized strings in a client application, you must either set the **Language** property on the object, or pass a **Culture** or **Locale Identifier** parameter on the connection string (for example, by setting `LocaleIdentifier=1036` to return French strings).  
  
 Plan on using **Locale Identifier** if you want to support multiple, simultaneous translations of the same object in different languages. Setting the **Language** property works, but it also impacts processing and queries, which could have unintended consequences. Setting **Locale Identifier** is the better choice because it's only used to return translated strings.  
  
 A translation consists of a locale identifier (LCID), a translated caption for the object (for example, the dimension or attribute name), and optionally, a binding to a column that provides data values in the target language. You can have multiple translations, but you can only use one for any given connection. There is no theoretical limit on the number of translations you can embed in model, but each translation adds complexity to testing, and all translations must share the same collation, so when designing your solution keep these natural constraints in mind.  
  
> [!TIP]  
>  You can use client applications such as Excel, Management Studio, and SQL Server Profiler to return translated strings. See [Globalization Tips and Best Practices (Analysis Services)](../../Topics/TopicNameNotContainA/Globalization-Tips-and-Best-Practices--Analysis-Services-.md) for details.  
  
## How to add translated metadata to model in Analysis Services  
 Visit these links for step-by-step instructions:  
  
-   [Translations in Tabular models (Analysis Services)](../../Topics/TopicNameNotContainA/Translations-in-Tabular-models--Analysis-Services-.md)  
  
-   [Translations in Multidimensional Models (Analysis Services)](../../Topics/TopicNameNotContainA/Translations-in-Multidimensional-Models--Analysis-Services-.md)  
  
## See Also  
 [Globalization scenarios for Analysis Services](../../Topics/TopicNameNotContainA/Globalization-scenarios-for-Analysis-Services.md)   
 [Languages and Collations (Analysis Services)](../../Topics/TopicNameNotContainA/Languages-and-Collations--Analysis-Services-.md)   
 [Set or Change the Column Collation](../../Topics/TopicNameNotContainA/Set-or-Change-the-Column-Collation.md)   
 [Globalization Tips and Best Practices (Analysis Services)](../../Topics/TopicNameNotContainA/Globalization-Tips-and-Best-Practices--Analysis-Services-.md)