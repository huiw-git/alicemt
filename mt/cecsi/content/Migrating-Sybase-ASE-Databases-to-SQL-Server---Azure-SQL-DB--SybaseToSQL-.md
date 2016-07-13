---
title: Migrating Sybase ASE Databases to SQL Server - Azure SQL DB (SybaseToSQL)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
manager:lonnyb
---
# Migrating Sybase ASE Databases to SQL Server - Azure SQL DB (SybaseToSQL)
SQL Server Migration Assistant (SSMA) for Sybase is a comprehensive environment that helps you quickly migrate Sybase Adaptive Server Enterprise (ASE) databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB. By using SSMA for Sybase, you can review database objects and data, assess databases for migration, migrate database objects to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB, and then migrate data to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB.  
  
## Recommended Migration Process  
To successfully migrate objects and data from ASE databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB, use the following process:  
  
1.  [Create a new SSMA project](assetId:///11091d95-c488-48c3-891a-743cac94ac93).  
  
    After you create the project, you can set project conversion, migration, and type mapping options. For information about project settings, see [Setting Project Options &#40;SybaseToSQL&#41;](../content/Setting-Project-Options--SybaseToSQL-.md). For information about customizing data type mappings, see [Mapping Sybase ASE and SQL Server Data Types &#40;SybaseToSQL&#41;](../content/Mapping-Sybase-ASE-and-SQL-Server-Data-Types--SybaseToSQL-.md).  
  
2.  [Connect to the Sybase ASE database server](assetId:///a45a2330-9175-4c9e-af38-ef920e350614).  
  
3.  [Connect to an instance SQL Server](assetId:///dd368a1a-45b0-40e9-b4d3-5cdb48c26606) or [Connect to an instance of Azure SQL DB](assetId:///9e77e4b0-40c0-455c-8431-ca5d43849aa7).  
  
4.  [Map ASE database schemas to SQL Server/ Azure SQL DB database schemas](assetId:///2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Optionally, [create assessment reports](assetId:///eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) to assess database objects for conversion and estimate the conversion time.  
  
6.  [Convert Sybase ASE database schemas into SQL Server/ Azure SQL DB schemas](assetId:///509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Load the converted database objects into SQL Server/ Azure SQL DB](assetId:///4c59256f-99a8-4351-9559-a455813dbd06).  
  
    You can by either save a script and run it in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or Azure SQL DB, or you can synchronize the database objects.  
  
8.  [Migrate data to SQL Server/ Azure SQL DB](assetId:///54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. If necessary, update your database applications.  
  
## See Also  
[Installing SSMA  for Sybase &#40;SybaseToSQL&#41;](../content/Installing-SSMA--for-Sybase--SybaseToSQL-.md)  
[Getting Started with SSMA for Sybase &#40;SybaseToSQL&#41;](../content/Getting-Started-with-SSMA-for-Sybase--SybaseToSQL-.md)  
  
