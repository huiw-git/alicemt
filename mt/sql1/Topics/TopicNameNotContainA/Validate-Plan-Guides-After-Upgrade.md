---
title: "Validate Plan Guides After Upgrade"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-plan-guides
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Validate Plan Guides After Upgrade
We recommend re-evaluating and testing plan guide definitions when you upgrade your application to a new release of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Performance tuning requirements and plan guide matching behavior may change. Although an invalid plan guide will not cause a query to fail, the plan is compiled without using the plan guide and may not be the best choice. After upgrading a database to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], we recommend that you perform the following tasks:  
  
-   Validate existing plan guides by using the [sys.fn_validate_plan_guide](assetId:///3af8b47a-936d-4411-91d1-d2d16dda5623) function.  
  
-   Use extended events to monitor for misguided plans for some period of time by using the [Plan Guide Unsuccessful](../../Topics/TopicNameNotContainA/Plan-Guide-Unsuccessful-Event-Class.md) event.