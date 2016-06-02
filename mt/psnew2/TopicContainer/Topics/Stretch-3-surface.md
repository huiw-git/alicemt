---
title: Stretch 3 surface
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1342d0c5-a342-443a-b851-eb814a8b9ca7
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Stretch 3 surface
Learn about blocking issues that you have to resolve before you can enable Stretch Database.

## <a name="Limitations"></a>Blocking issues
In [!INCLUDE[ssSQL15](../Token/ssSQL15_md.md)], the following items make a table ineligible for Stretch.

**Table properties**
-   More than 1,023 columns

-   More than 998 indexes

-   Tables that contain FILESTREAM data

-   FileTables

-   Replicated tables

-   Tables that are actively using Change Tracking or Change Data Capture

-   Memory\-optimized tables

**Data types and column properties**
-   timestamp

-   sql\_variant

-   XML

-   geometry

-   geography

-   hierarchyid

-   CLR user\-defined types (UDTs)

**Column types**
-   COLUMN\_SET

-   Computed columns

**Constraints**
-   Check constraints

-   Default constraints

-   Foreign key constraints that reference the table

**Indexes**
-   Full text indexes

-   XML indexes

-   Spatial indexes

-   Indexed views that reference the table

## <a name="Caveats"></a>Limitations and caveats for Stretch\-enabled tables
In [!INCLUDE[ssSQL15](../Token/ssSQL15_md.md)], Stretch\-enabled tables have the following limitations or caveats.

-   Uniqueness is not enforced for UNIQUE constraints and PRIMARY KEY constraints on a Stretch\-enabled table.

-   You can't run UPDATE or DELETE operations on a Stretch\-enabled table.

-   You can't INSERT into the remote Azure SQL Database table.

-   You can't create an index for a view that includes Stretch\-enabled tables.

-   You can't update or delete from a view that includes Stretch\-enabled tables. You can, however, insert into a view that includes Stretch\-enabled tables.

-   Filters on indexes are not propagated to the remote table.

## See Also
[Identify databases and tables for Stretch Database by running Stretch Database Advisor](assetId:///81bd93d8-eef8-4572-88d7-5c37ab5ac2bf)
[Enable Stretch Database for a database](assetId:///37854256-8c99-4566-a552-432e3ea7c6da)
[Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc)

