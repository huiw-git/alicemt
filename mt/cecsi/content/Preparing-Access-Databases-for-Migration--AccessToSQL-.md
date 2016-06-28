---
title: Preparing Access Databases for Migration (AccessToSQL)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114
---
# Preparing Access Databases for Migration (AccessToSQL)
Before you migrate Access databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], you must determine which databases to migrate, and then make sure those databases are ready for migration.  
  
## Determining When to Migrate to SQL Server  
The Jet database engine, which is used as the database engine for Access, is a flexible, easy\-to\-use solution for data management. However, as databases become larger and more mission critical, many users find that they require greater performance, security, or availability. For applications that require a more robust data platform, consider moving the underlying databases for those applications to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. For more information about deciding when to migrate, see the [migration information page](http://go.microsoft.com/fwlink/?LinkId=68571) on the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Web site.  
  
After you migrate databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], you can continue to use Access by using linked tables, or you can manually migrate your applications to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] .NET Framework\-based code that interacts directly with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
## Determining Which Databases to Migrate  
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Migration Assistant (SSMA) for Access can locate Access databases for you. You can then export metadata about those databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. For more information about how to export and query metadata, see [Exporting an Access Inventory](assetId:///7e1941fb-3d14-4265-aff6-c77a4026d0ed).  
  
**Note** Not all Access features and settings are supported by, or can be easily converted to, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. Before you start migrating databases, see [Incompatible Access Features](assetId:///99d45b9c-e3b9-4d56-8c25-b594b887ace1).  
  
## Preparing for Migration  
Use the following guidelines to help you prepare your Access databases for migration to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
### Upgrading Older Access Databases  
SSMA for Access supports Access 97 and later versions. If you have databases from earlier versions of Access, open and save the databases in Access 97 or a later version. For more information about how to convert Access databases to a later version, see the [Converting Access Databases](http://go.microsoft.com/fwlink/?LinkId=65279) page at the Office Online Web site.  
  
### Removing Workgroup Protection  
SSMA cannot migrate databases that use workgroup protection. You can do the following to remove workgroup protection from an Access database:  
  
1.  Copy the Access database file to another location.  
  
2.  Open the copied database.  
  
3.  On the **Tools** menu, point to **Security**, and then select **User and Group Permissions**.  
  
4.  Select the **Users** option, select the **Admin** user, and then make sure that the **Administer** permission is selected.  
  
5.  Select the **Groups** option, select the **Users** group, and then make sure that the **Administer** permission is selected.  
  
6.  Click **OK**, and then on the **File** menu, click **Exit**.  
  
You can now use SSMA to migrate the copied database. After you load the schema into [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], you can manually secure the database on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
### Backing Up Databases  
Before you migrate your Access databases to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], you should back up the Access databases that you will be migrating and the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] databases into which you will migrate Access objects and data.  
  
To back up an Access database, on the **Tools** menu, point to **Database Utilities**, and then select **Back Up Database**.  
  
For information about how to  back up [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] databases, see "Backing Up and Restoring Databases in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
### Documenting Databases  
You might also want to document properties of your Access databases, such as lists of database objects, file sizes, and permissions. To generate this documentation in Access, on the **Tools** menu, point to **Analyze**, and then click **Documenter**.  
  
## See Also  
[Migrating Access Databases to SQL Server](assetId:///76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Linking Access Applications to SQL Server](assetId:///82374ad2-7737-4164-a489-13261ba393d4)  
  
