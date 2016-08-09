---
title: "Change Tracking (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Change Tracking (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], you can use change tracking groups to take action when an attribute value changes. Use change tracking when you don’t know what the new value will be, but instead want to know if any change occurred.  
  
## Configuring Change Tracking  
 To configure change tracking, you add an attribute to a change tracking group. The group can contain one or many attributes. Then, you create a business rule to define the action that is taken when any of the attributes in the group change.  
  
> [!NOTE]  
>  Change tracking business rules consider staged (imported) data to be changed.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Add attributes to a change tracking group.|[Add Attributes to a Change Tracking Group (Master Data Services)](../../Topics/TopicNameContainA/Add-Attributes-to-a-Change-Tracking-Group--Master-Data-Services-.md)|  
|Create a business rule that initiates actions based on attribute changes.|[Initiate Actions Based on Attribute Value Changes (Master Data Services)](../../Topics/TopicNameNotContainA/Initiate-Actions-Based-on-Attribute-Value-Changes--Master-Data-Services-.md)|  
  
## Related Content  
  
-   [Validation (Master Data Services)](../../Topics/TopicNameNotContainA/Validation--Master-Data-Services-.md)  
  
-   [Business Rules (Master Data Services)](../../Topics/TopicNameNotContainA/Business-Rules--Master-Data-Services-.md)  
  
-   [Attributes (Master Data Services)](../../Topics/TopicNameNotContainA/Attributes--Master-Data-Services-.md)