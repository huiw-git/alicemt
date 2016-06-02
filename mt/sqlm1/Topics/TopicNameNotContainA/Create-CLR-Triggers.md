---
title: Create CLR Triggers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-dml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
---
# Create CLR Triggers
  You can create a database object inside [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] common language runtime \(CLR\). Database objects that can leverage the rich programming model provided by the CLR include DML triggers, DDL triggers, stored procedures, functions, aggregate functions, and types.  
  
 Creating a CLR trigger \(DML or DDL\) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] involves the following steps:  
  
-   Define the trigger as a class in a .NET Framework\-supported language. For more information about how to program triggers in the CLR, see [CLR Triggers](../Topic/CLR%20Triggers.md). Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] using the appropriate language compiler.  
  
-   Register the assembly in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using the CREATE ASSEMBLY statement. For more information about assemblies in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Assemblies &#40;Database Engine&#41;](../Topic/Assemblies%20\(Database%20Engine\).md).  
  
-   Create the trigger that references the registered assembly.  
  
> [!NOTE]  
>  Deploying a SQL Server Project in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)] registers an assembly in the database that was specified for the project. Deploying the project also creates CLR triggers in the database for all methods annotated with the **SqlTrigger** attribute. For more information, see [Deploying CLR Database Objects](../Topic/Deploying%20CLR%20Database%20Objects.md).  
  
> [!NOTE]  
>  The ability of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to execute CLR code is off by default. You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] unless the [clr enabled Option](../../Topics\TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md) is enabled using [sp\_configure \(Transact\-SQL\)](../Topic/sp_configure%20\(Transact-SQL\).md).  
  
 **To create, modify, or drop an assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASSEMBLY%20\(Transact-SQL\).md)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../Topic/ALTER%20ASSEMBLY%20\(Transact-SQL\).md)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](../Topic/DROP%20ASSEMBLY%20\(Transact-SQL\).md)  
  
 **To create a CLR trigger**  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](../Topic/CREATE%20TRIGGER%20\(Transact-SQL\).md)  
  
## See Also  
 [DML Triggers](../../Topics\TopicNameNotContainA/DML-Triggers.md)   
 [Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](../Topic/Common%20Language%20Runtime%20\(CLR\)%20Integration%20Programming%20Concepts.md)   
 [Data Access from CLR Database Objects](../Topic/Data%20Access%20from%20CLR%20Database%20Objects.md)  
  
  