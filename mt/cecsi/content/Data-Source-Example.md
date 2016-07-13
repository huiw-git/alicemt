---
title: Data Source Example
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Data Source Example
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>On computers running Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional, or Microsoft Windows® 95/98, machine data source information is stored in the registry. Depending on which registry key the information is stored under, the data source is known as a <legacyItalic>user data source</legacyItalic> or a <legacyItalic>system data source</legacyItalic>. User data sources are stored under the HKEY_CURRENT_USER key and are available only to the current user. System data sources are stored under the HKEY_LOCAL_MACHINE key and can be used by more than one user on one machine. They can also be used by systemwide services, which can then gain access to the data source even if no user is logged on to the machine. For more information about user and system data sources, see <legacyLink xlink:href="ac6d186f-b394-406c-94c4-c6331d1ca468">SQLManageDataSources</legacyLink>.</para>
    <para>Suppose a user has three user data sources: Personnel and Inventory, which use an Oracle DBMS; and Payroll, which uses a Microsoft SQL Server DBMS. The registry values for data sources might be:</para>
    <code>HKEY_CURRENT_USER
SOFTWARE
          ODBC
               Odbc.ini
                    ODBC Data Sources
                    Personnel : REG_SZ : Oracle
                    Inventory : REG_SZ : Oracle
                    Payroll : REG_SZ : SQL Server</code>
    <para>and the registry values for the Payroll data source might be:</para>
    <code>HKEY_CURRENT_USER
     SOFTWARE
          ODBC
               Odbc.ini
                    Payroll
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll
                         Description : REG_SZ : Payroll database
                         Server : REG_SZ : PYRLL1
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes
                         OEMTOANSI : REG_SZ : No
                         LastUser : REG_SZ : smithjo
                         Database : REG_SZ : Payroll
                         Language : REG_SZ :</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>