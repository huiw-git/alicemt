---
title: "Create User-defined Aggregates"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-udf
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c278b746-6323-4b32-b460-239915acc067
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# Create User-defined Aggregates
You can create a database object inside [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is programmed in a CLR assembly. Database objects that can leverage the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.  
  
 Like the built-in aggregate functions provided in [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], user-defined aggregate functions perform a calculation on a set of values and return a single value.  
  
 Creating a user-defined aggregate function in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] involves the following steps:  
  
-   Define the user-defined aggregate function as a class in a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] .NET Framework-supported language. For more information about how to program user-defined aggregates in the CLR, see [Database Engine .NET Framework Programming Concepts](assetId:///bad9b7e8-5967-4afa-8dc8-6d840faf9372). Compile this class to build a CLR assembly using the appropriate language compiler.  
  
-   Register the assembly in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using the CREATE ASSEMBLY statement. For more information about assemblies in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Assemblies](assetId:///4b146437-3061-47f6-9e8c-26eeea10b54e).  
  
-   Create the user-defined aggregate that references the registered assembly using the CREATE AGGREGATE statement.  
  
> [!NOTE]  
>  Deploying a SQL Server Project in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)] registers an assembly in the database that was specified for the project. Deploying the project also creates a user-defined aggregate in the database for all class definitions annotated with the **SqlUserDefinedAggregate** attribute. For more information, see [Deploying CLR Database Objects](assetId:///00752573-3367-41a7-af98-7b7a29e8e2f2).  
  
> [!NOTE]  
>  The ability of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to execute CLR code is off by default. You can create, alter and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] unless the [clr enabled Option](../../Topics/TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md) is enabled using [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8).  
  
 **To create, modify, or drop an assembly**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](assetId:///d8d1d245-c2c3-4325-be52-4fc1122c2079)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](assetId:///87bca678-4e79-40e1-bb8b-bd5ed8f34853)  
  
-   [DROP ASSEMBLY (Transact-SQL)](assetId:///452d181a-a8e6-44a3-975d-29966d01b18d)  
  
 **To create a user-defined aggregate**  
  
-   [CREATE AGGREGATE (Transact-SQL)](assetId:///62eebc19-9f15-4245-94fa-b3fcd64a9d42)  
  
## See Also  
 [Database Engine .NET Framework Programming](assetId:///951bf851-3e6e-4361-ae6a-2bcd5b837ebd)