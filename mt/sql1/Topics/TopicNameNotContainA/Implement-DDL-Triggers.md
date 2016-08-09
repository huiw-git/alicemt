---
title: "Implement DDL Triggers"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-ddl
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f44e5340-1d18-40e9-828e-0ffcca091ae3
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# Implement DDL Triggers
This topic provides information to help you create DDL triggers, modify DDL triggers, and disable or drop DDL triggers.  
  
## Creating DDL Triggers  
 DDL triggers are created by using the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] CREATE TRIGGER statement for DDL triggers.  
  
 **To create a DDL trigger**  
  
-   [Understanding DDL Triggers](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7)  
  
> [!IMPORTANT]  
>  The ability to return result sets from triggers will be removed in a future version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them. Avoid returning result sets from triggers in new development work, and plan to modify applications that currently do this. To prevent triggers from returning result sets in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], set the [disallow results from triggers Option](../../Topics/TopicNameNotContainA/disallow-results-from-triggers-Server-Configuration-Option.md) to 1. The default setting of this option will be 1 in a future version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
## Modifying DDL Triggers  
 If you have to modify the definition of a DDL trigger, you can either drop and re-create the trigger or redefine the existing trigger in a single step.  
  
 If you change the name of an object that is referenced by a DDL trigger, you must modify the trigger so that its text reflects the new name. Therefore, before renaming an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.  
  
 A trigger can also be modified to encrypt its definition.  
  
 **To modify a trigger**  
  
-   [ALTER TRIGGER](assetId:///2a99c7c1-ac2f-4637-aa7c-3d1bf514e500)  
  
 **To view the dependencies of a trigger**  
  
-   [sys.sql_expression_dependencies (Transact-SQL)](assetId:///78a218e4-bf99-4a6a-acbf-ff82425a5946)  
  
-   [sys.dm_sql_referenced_entities](assetId:///077111cb-b860-4d61-916f-bac5d532912f)  
  
-   [sys.dm_sql_referencing_entities](assetId:///c16f8f0a-483f-4feb-842e-da90426045ae)  
  
## Disabling and Dropping DDL Triggers  
 When a DDL trigger is no longer needed, you can disable it or delete it.  
  
 Disabling a DDL trigger does not drop it. The trigger still exists as an object in the current database. However, the trigger will not fire when any [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements on which it was programmed are run. DDL triggers that are disabled can be reenabled. Enabling a DDL trigger causes it to fire in the same way the trigger did when it was originally created. When DDL triggers are created, they are enabled by default.  
  
 When a DDL trigger is deleted, it is dropped from the current database. Any objects or data upon which the DDL trigger is scoped are not affected.  
  
 **To disable a DDL trigger**  
  
-   [DISABLE TRIGGER](assetId:///e6529f06-e442-437e-a7bf-41790bc092c5)  
  
-   [ALTER TABLE](assetId:///f1745145-182d-4301-a334-18f799d361d1)  
  
 **To enable a DDL trigger**  
  
-   [ENABLE TRIGGER](assetId:///6e21f0ad-68d0-432f-9c7c-a119dd2d3fc9)  
  
-   [ALTER TABLE](assetId:///f1745145-182d-4301-a334-18f799d361d1)  
  
 **To delete a DDL trigger**  
  
-   [DROP TRIGGER](assetId:///092d0d71-9f1e-4e38-a1c4-2487adfa5b4e)