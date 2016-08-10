---
title: "Create CLR Functions"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-udf
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a82df075-2243-4e19-bfe1-ae6d65dabd0f
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# Create CLR Functions
You can create a database object inside an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] common language runtime (CLR). Database objects that can leverage the rich programming model provided by the common language runtime include aggregate functions, functions, stored procedures, triggers, and types.  
  
 Creating a CLR function in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] involves the following steps:  
  
-   Define the function as a static method of a class in a language supported by the [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)]. For more information about how to program functions in the common language runtime, see [Database Engine .NET Framework Programming Concepts](assetId:///6f7491f1-9a46-4146-ae09-056248634de2). Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] by using the appropriate language compiler.  
  
-   Register the assembly in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] by using the CREATE ASSEMBLY statement. For more information about assemblies in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Assemblies](assetId:///4b146437-3061-47f6-9e8c-26eeea10b54e).  
  
-   Create the function that references the registered assembly by using the [CREATE FUNCTION](assetId:///864b393f-225f-4895-8c8d-4db59ea60032) statement.  
  
> [!NOTE]  
>  Deploying a SQL Server Project in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)] registers an assembly in the database that was specified for the project. Deploying the project also creates CLR functions in the database for all methods annotated with the **SqlFunction** attribute. For more information, see [Deploying CLR Database Objects](assetId:///00752573-3367-41a7-af98-7b7a29e8e2f2).  
  
> [!NOTE]  
>  The ability of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to execute CLR code is off by default. You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] unless the [clr enabled Option](../../Topics/TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md) is enabled by using [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8).  
  
## Accessing External Resources  
 CLR functions can be used to access external resources such as files, network resources, Web Services, other databases (including remote instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]). This can be achieved by using various classes in the [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)], such as `System.IO`, `System.WebServices`, `System.Sql`, and so on. The assembly that contains such functions should at least be configured with the EXTERNAL_ACCESS permission set for this purpose. For more information, see [CREATE ASSEMBLY (Transact-SQL)](assetId:///d8d1d245-c2c3-4325-be52-4fc1122c2079). The SQL Client Managed Provider can be used to access remote instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. However, loopback connections to the originating server are not supported in CLR functions.  
  
 **To create, modify, or drop assemblies in SQL Server**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](assetId:///d8d1d245-c2c3-4325-be52-4fc1122c2079)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](assetId:///87bca678-4e79-40e1-bb8b-bd5ed8f34853)  
  
-   [DROP ASSEMBLY (Transact-SQL)](assetId:///452d181a-a8e6-44a3-975d-29966d01b18d)  
  
 **To create a CLR function**  
  
-   [CREATE FUNCTION (Transact-SQL)](assetId:///864b393f-225f-4895-8c8d-4db59ea60032)  
  
## Accessing Native Code  
 CLR functions can be used to access native (unmanaged) code, such as code written in C or C++, via the use of PInvoke from managed code (see [Calling Native Functions from Managed Code](http://go.microsoft.com/fwlink/?LinkID=181929) for details). This can allow you to re-use legacy code as CLR UDFs, or write performance-critical UDFs in native code. This requires using an UNSAFE assembly. See [CLR Integration Code Access Security](assetId:///2111cfe0-d5e0-43b1-93c3-e994ac0e9729) for cautions about use of UNSAFE assemblies.  
  
## See Also  
 [Create User-defined Functions (Database Engine)](../../Topics/TopicNameNotContainA/Create-User-defined-Functions--Database-Engine-.md)   
 [Create User-defined Aggregates](../../Topics/TopicNameNotContainA/Create-User-defined-Aggregates.md)   
 [Execute User-defined Functions](../../Topics/TopicNameNotContainA/Execute-User-defined-Functions.md)   
 [View User-defined Functions](../../Topics/TopicNameNotContainA/View-User-defined-Functions.md)   
 [Database Engine .NET Framework Programming](assetId:///951bf851-3e6e-4361-ae6a-2bcd5b837ebd)