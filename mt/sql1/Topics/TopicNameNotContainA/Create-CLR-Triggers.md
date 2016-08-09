---
title: "Create CLR Triggers"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-dml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# Create CLR Triggers
You can create a database object inside [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] common language runtime (CLR). Database objects that can leverage the rich programming model provided by the CLR include DML triggers, DDL triggers, stored procedures, functions, aggregate functions, and types.  
  
 Creating a CLR trigger (DML or DDL) in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] involves the following steps:  
  
-   Define the trigger as a class in a .NET Framework-supported language. For more information about how to program triggers in the CLR, see [Data Access from CLR Database Objects](assetId:///302a4e4a-3172-42b6-9cc0-4a971ab49c1c). Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] using the appropriate language compiler.  
  
-   Register the assembly in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using the CREATE ASSEMBLY statement. For more information about assemblies in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Assemblies](assetId:///4b146437-3061-47f6-9e8c-26eeea10b54e).  
  
-   Create the trigger that references the registered assembly.  
  
> [!NOTE]  
>  Deploying a SQL Server Project in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)] registers an assembly in the database that was specified for the project. Deploying the project also creates CLR triggers in the database for all methods annotated with the **SqlTrigger** attribute. For more information, see [Deploying CLR Database Objects](assetId:///00752573-3367-41a7-af98-7b7a29e8e2f2).  
  
> [!NOTE]  
>  The ability of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to execute CLR code is off by default. You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] unless the [clr enabled Option](../../Topics/TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md) is enabled using [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8).  
  
 **To create, modify, or drop an assembly**  
  
-   [CREATE ASSEMBLY](assetId:///d8d1d245-c2c3-4325-be52-4fc1122c2079)  
  
-   [ALTER ASSEMBLY](assetId:///87bca678-4e79-40e1-bb8b-bd5ed8f34853)  
  
-   [DROP ASSEMBLY](assetId:///452d181a-a8e6-44a3-975d-29966d01b18d)  
  
 **To create a CLR trigger**  
  
-   [CREATE TRIGGER](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7)  
  
## See Also  
 [DML Triggers](../../Topics/TopicNameNotContainA/DML-Triggers.md)   
 [Database Engine .NET Framework Programming](assetId:///951bf851-3e6e-4361-ae6a-2bcd5b837ebd)   
 [Data Access from CLR Database Objects](assetId:///9a0f4dee-71c1-42e9-a85e-52382807010f)