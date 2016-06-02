---
title: Publication Properties, General
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
---
# Publication Properties, General
  The **General** page of the **Publication Properties** dialog box contains basic information on the publication, including name, description, and the subscription expiration policy.  
  
## Options  
 **Name**  
 The name of the publication \(read\-only\).  
  
 **Database**  
 The name of the publication database \(read\-only\).  
  
 **Description**  
 The description of the publication.  
  
 **Type**  
 The type of publication \(read\-only\).  
  
 **Subscription expiration**  
 Select one of the options for subscription expiration: **Subscriptions never expire** or **Subscriptions expire**, with an explicit time period \(**Interval**\).  
  
 For snapshot and transactional publications, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you accept the default of **Subscriptions never expire**.  
  
 For merge replication, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you accept the default of **Subscriptions expire** and set as low a value as possible for **Interval**. As the subscription expiration period increases, so does the amount of metadata stored, which can affect performance. Balance the need for Subscribers to be disconnected or simply not to synchronize for an extended period against the potential performance issues of storing and processing a large amount of metadata.  
  
 For more information, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
 **Compatibility level**  
 [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions only; merge publications only. Select the minimum [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version required for Subscribers that synchronize with this publication. There are a number of rules associated with determining the compatibility level.  
  
## See Also  
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)  
  
  