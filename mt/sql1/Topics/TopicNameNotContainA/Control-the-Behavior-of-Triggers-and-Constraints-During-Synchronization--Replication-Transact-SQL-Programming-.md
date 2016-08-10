---
title: "Control the Behavior of Triggers and Constraints During Synchronization (Replication Transact-SQL Programming)"
ms.custom: na
ms.date: 08/09/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# Control the Behavior of Triggers and Constraints During Synchronization (Replication Transact-SQL Programming)
During synchronization, replication agents execute [Controlling Constraints, Identities, and Triggers with NOT FOR REPLICATION](assetId:///1054c76e-0fd5-4131-8c07-a6c5d024af50), [UPDATE](assetId:///40e63302-0c68-4593-af3e-6d190181fee7), and [DELETE](assetId:///ed6b2105-0f35-408f-ba51-e36ade7ad5b2) statements on replicated tables, which can cause data manipulation language (DML) triggers on these tables to be executed. There are cases when you may need to prevent these triggers from firing or constraints from being enforced during synchronization. This behavior depends on how the trigger or constraint is created.  
  
### To prevent triggers from executing during synchronization  
  
1.  When creating a new trigger, specify the NOT FOR REPLICATION option of [CREATE TRIGGER](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7).  
  
2.  For an existing trigger, specify the NOT FOR REPLICATION option of [ALTER TRIGGER](assetId:///2a99c7c1-ac2f-4637-aa7c-3d1bf514e500).  
  
### To prevent constraints from being enforced during synchronization  
  
1.  When creating a new CHECK or FOREIGN KEY constraint, specify CHECK NOT FOR REPLICATION option in the constraint definition of [CREATE TABLE](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b).  
  
## See Also  
 [Create Tables (Database Engine)](../../Topics/TopicNameNotContainA/Create-Tables--Database-Engine-.md)