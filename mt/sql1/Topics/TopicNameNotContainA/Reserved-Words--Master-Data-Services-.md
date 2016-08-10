---
title: "Reserved Words (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# Reserved Words (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], when you create model objects or members, some words cannot be used. Using these words may cause errors.  
  
> [!NOTE]  
>  You should also limit your use of special characters (symbols, hyphenation, etc.).  
  
-   [Models](../../Topics/TopicNameNotContainA/Reserved-Words--Master-Data-Services-.md#models)  
  
-   [Entities](../../Topics/TopicNameNotContainA/Reserved-Words--Master-Data-Services-.md#entities)  
  
-   [Explicit Hierarchies](../../Topics/TopicNameNotContainA/Reserved-Words--Master-Data-Services-.md#exhierarchies)  
  
-   [Attributes](../../Topics/TopicNameNotContainA/Reserved-Words--Master-Data-Services-.md#attributes)  
  
-   [Members](../../Topics/TopicNameNotContainA/Reserved-Words--Master-Data-Services-.md#members)  
  
##  <a name="models"></a> Models  
 If you create a model with the name set to **Name** or **Code**, do not select **Create entity with same name as model** because **Name** or **Code** cannot be used for the name of an entity.  
  
##  <a name="entities"></a> Entities  
 For entity names, you cannot use **Name** or **Code**.  
  
##  <a name="exhierarchies"></a> Explicit Hierarchies  
 For explicit hierarchy names, you cannot use **Name** or **Code**.  
  
##  <a name="attributes"></a> Attributes  
  
-   **ID**  
  
-   **Code**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **Name**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> Members  
 For members, you cannot use **MDMMemberStatus**, **MDMUnused**, or **ROOT** for the **Code** attribute value.  
  
## See Also  
 [Master Data Services Overview (MDS)](../../Topics/TopicNameNotContainA/Master-Data-Services-Overview--MDS-.md)