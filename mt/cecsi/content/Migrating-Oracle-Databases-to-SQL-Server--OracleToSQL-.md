---
title: Migrating Oracle Databases to SQL Server (OracleToSQL)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
manager:b-tomb
---
# Migrating Oracle Databases to SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Migration Assistant (SSMA) for Oracle is a comprehensive environment that helps you quickly migrate Oracle databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB. By using SSMA for Oracle, you can review database objects and data, assess databases for migration, migrate database objects to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB, and then migrate data to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB. Note that you cannot migrate SYS and SYSTEM Oracle schemas.  
  
## Recommended Migration Process  
To successfully migrate objects and data from Oracle databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB, use the following process:  
  
1.  [Create a new SSMA project](assetId:///ee5d94c0-c7a6-4779-bd32-729bdaf61e1b).  
  
    After you create the project, you can set project conversion, migration, and type mapping options. For information about project settings, see [Setting Project Options &#40;OracleToSQL&#41;](../content/Setting-Project-Options--OracleToSQL-.md). For information about how to customize data type mappings, see [Mapping Oracle and SQL Server Data Types &#40;OracleToSQL&#41;](../content/Mapping-Oracle-and-SQL-Server-Data-Types--OracleToSQL-.md).  
  
2.  [Connect to the Oracle database server](assetId:///e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
3.  [Connect to an instance of SQL Server](assetId:///1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
4.  [Map Oracle database schemas to SQL Server database schemas](assetId:///0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc).  
  
5.  Optionally, [Create assessment reports](assetId:///4de9bcf6-1346-4740-87f9-7f24a8226357) to assess database objects for conversion and estimate the conversion time.  
  
6.  [Convert Oracle database schemas into SQL Server schemas](assetId:///e021182d-31da-443d-b110-937f5db27272).  
  
7.  [Load the converted database objects into SQL Server](assetId:///a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
    You can do this in one of the following ways:  
  
    -   Save a script and run it in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
    -   Synchronize the database objects.  
  
8.  [Migrate data to SQL Server](assetId:///e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
9. If necessary, update database applications.  
  
## See Also  
[Installing SSMA  for Oracle &#40;OracleToSQL&#41;](../content/Installing-SSMA--for-Oracle--OracleToSQL-.md)  
[Getting Started with SSMA for Oracle &#40;OracleToSQL&#41;](../content/Getting-Started-with-SSMA-for-Oracle--OracleToSQL-.md)  
  
