---
title: Create CLR Functions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-udf
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a82df075-2243-4e19-bfe1-ae6d65dabd0f
---
# Create CLR Functions
  You can create a database object inside an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] common language runtime \(CLR\). Database objects that can leverage the rich programming model provided by the common language runtime include aggregate functions, functions, stored procedures, triggers, and types.  
  
 Creating a CLR function in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] involves the following steps:  
  
-   Define the function as a static method of a class in a language supported by the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)]. For more information about how to program functions in the common language runtime, see [CLR User-Defined Functions](../Topic/CLR%20User-Defined%20Functions.md). Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] by using the appropriate language compiler.  
  
-   Register the assembly in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using the CREATE ASSEMBLY statement. For more information about assemblies in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Assemblies &#40;Database Engine&#41;](../Topic/Assemblies%20\(Database%20Engine\).md).  
  
-   Create the function that references the registered assembly by using the [CREATE FUNCTION](../Topic/CREATE%20FUNCTION%20\(Transact-SQL\).md) statement.  
  
> [!NOTE]  
>  Deploying a SQL Server Project in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)] registers an assembly in the database that was specified for the project. Deploying the project also creates CLR functions in the database for all methods annotated with the **SqlFunction** attribute. For more information, see [Deploying CLR Database Objects](../Topic/Deploying%20CLR%20Database%20Objects.md).  
  
> [!NOTE]  
>  The ability of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to execute CLR code is off by default. You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] unless the [clr enabled Option](../../Topics\TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md) is enabled by using [sp\_configure \(Transact\-SQL\)](../Topic/sp_configure%20\(Transact-SQL\).md).  
  
## Accessing External Resources  
 CLR functions can be used to access external resources such as files, network resources, Web Services, other databases \(including remote instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\). This can be achieved by using various classes in the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)], such as `System.IO`, `System.WebServices`, `System.Sql`, and so on. The assembly that contains such functions should at least be configured with the EXTERNAL\_ACCESS permission set for this purpose. For more information, see [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASSEMBLY%20\(Transact-SQL\).md). The SQL Client Managed Provider can be used to access remote instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. However, loopback connections to the originating server are not supported in CLR functions.  
  
 **To create, modify, or drop assemblies in SQL Server**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASSEMBLY%20\(Transact-SQL\).md)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../Topic/ALTER%20ASSEMBLY%20\(Transact-SQL\).md)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](../Topic/DROP%20ASSEMBLY%20\(Transact-SQL\).md)  
  
 **To create a CLR function**  
  
-   [CREATE FUNCTION &#40;Transact-SQL&#41;](../Topic/CREATE%20FUNCTION%20\(Transact-SQL\).md)  
  
## Accessing Native Code  
 CLR functions can be used to access native \(unmanaged\) code, such as code written in C or C\+\+, via the use of PInvoke from managed code \(see [Calling Native Functions from Managed Code](http://go.microsoft.com/fwlink/?LinkID=181929) for details\). This can allow you to re\-use legacy code as CLR UDFs, or write performance\-critical UDFs in native code. This requires using an UNSAFE assembly. See [CLR Integration Code Access Security](../Topic/CLR%20Integration%20Code%20Access%20Security.md) for cautions about use of UNSAFE assemblies.  
  
## See Also  
 [Create User-defined Functions &#40;Database Engine&#41;](../Topic/Create%20User-defined%20Functions%20\(Database%20Engine\).md)   
 [Create User-defined Aggregates](../../Topics\TopicNameNotContainA/Create-User-defined-Aggregates.md)   
 [Execute User-defined Functions](../../Topics\TopicNameNotContainA/Execute-User-defined-Functions.md)   
 [View User-defined Functions](../../Topics\TopicNameNotContainA/View-User-defined-Functions.md)   
 [Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](../Topic/Common%20Language%20Runtime%20\(CLR\)%20Integration%20Programming%20Concepts.md)  
  
  