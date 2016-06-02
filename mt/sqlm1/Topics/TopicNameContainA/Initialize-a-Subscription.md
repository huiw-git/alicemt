---
title: Initialize a Subscription
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
---
# Initialize a Subscription
  Subscribers in a replication topology must be initialized, so that they have a copy of the schema from each article in the publication they have subscribed to and any replication objects that are required, such as stored procedures, triggers, and metadata tables. In addition, the Subscriber typically receives an initial dataset. The default initialization method uses a full snapshot that includes schema, replication objects, and data, but publications can also be initialized without a full snapshot.  
  
 For more information, see [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md) and [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
  