---
title: Create User-defined Aggregates
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-udf
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c278b746-6323-4b32-b460-239915acc067
---
# Create User-defined Aggregates
  You can create a database object inside [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is programmed in a CLR assembly. Database objects that can leverage the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.  
  
 Like the built\-in aggregate functions provided in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], user\-defined aggregate functions perform a calculation on a set of values and return a single value.  
  
 Creating a user\-defined aggregate function in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] involves the following steps:  
  
-   Define the user\-defined aggregate function as a class in a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] .NET Framework\-supported language. For more information about how to program user\-defined aggregates in the CLR, see [CLR User-Defined Aggregates](../Topic/CLR%20User-Defined%20Aggregates.md). Compile this class to build a CLR assembly using the appropriate language compiler.  
  
-   Register the assembly in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using the CREATE ASSEMBLY statement. For more information about assemblies in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Assemblies &#40;Database Engine&#41;](../Topic/Assemblies%20\(Database%20Engine\).md).  
  
-   Create the user\-defined aggregate that references the registered assembly using the CREATE AGGREGATE statement.  
  
> [!NOTE]  
>  Deploying a SQL Server Project in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)] registers an assembly in the database that was specified for the project. Deploying the project also creates a user\-defined aggregate in the database for all class definitions annotated with the **SqlUserDefinedAggregate** attribute. For more information, see [Deploying CLR Database Objects](../Topic/Deploying%20CLR%20Database%20Objects.md).  
  
> [!NOTE]  
>  The ability of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to execute CLR code is off by default. You can create, alter and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] unless the [clr enabled Option](../../Topics\TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md) is enabled using [sp\_configure \(Transact\-SQL\)](../Topic/sp_configure%20\(Transact-SQL\).md).  
  
 **To create, modify, or drop an assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASSEMBLY%20\(Transact-SQL\).md)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../Topic/ALTER%20ASSEMBLY%20\(Transact-SQL\).md)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](../Topic/DROP%20ASSEMBLY%20\(Transact-SQL\).md)  
  
 **To create a user\-defined aggregate**  
  
-   [CREATE AGGREGATE &#40;Transact-SQL&#41;](../Topic/CREATE%20AGGREGATE%20\(Transact-SQL\).md)  
  
## See Also  
 [Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](../Topic/Common%20Language%20Runtime%20\(CLR\)%20Integration%20Programming%20Concepts.md)  
  
  