---
title: Stretch 2 identify
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e61524c-c9b5-466f-aa62-8004873be28a
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
# Stretch 2 identify
  To identify databases and tables that are candidates for Stretch Database, download SQL Server 2016 Upgrade Advisor and run the Stretch Database Advisor. Stretch Database Advisor also identifies blocking issues.

## Download and install Upgrade Advisor
 Download and install Upgrade Advisor from [here](http://go.microsoft.com/fwlink/?LinkID=613421). This tool is not included on the [!INCLUDE[ssSQL15]()] installation media.

## Run the Stretch Database Advisor

1.  Run Upgrade Advisor.

2.  Select **Scenarios**, and then select **RUN STRETCH DATABASE ADVISOR**.

3.  On the **Run Stretch Database Advisor** blade, click **SELECT DATABASES TO ANALYZE**.

4.  On the **Select databases** blade, click **SQL INSTANCE**.

5.  On the **Connect to SQL Instance** blade, enter the name of the [!INCLUDE[ssNoVersion](../Token/ssNoVersion_md.md)] instance. Then click **Connect**.

6.  On the **Select databases** blade, select the databases to analyze. Then click **Select**.

7.  On the **Run Stretch Database Advisor** blade, click **Run**.  The analysis runs.

## Review the results

1.  When the analysis is finished, on the **Stretch Database Advisor** blade, select one of the databases that you analyzed to display the **Analysis results** blade.

     The **Analysis results** blade lists recommended tables in the selected database that match the default recommendation criteria. Optionally, adjust the  minimum size and row count to expand or shrink the list of recommended tables.

2.  In the list of recommended tables on the **Analysis results** blade, select one of the recommended tables to display the **Table results** blade.

     The **Table results** blade lists the blocking issues for the selected table. For information about blocking issues detected by Stretch Database Advisor, see [Surface area limitations and blocking issues for Stretch Database](assetId:///2b1fbec1-7859-44fc-8417-724fc57a59c0).

3.  In the list of blocking issues on the **Table results** blade, select one of the issues to display the **Rule result** blade.

     The **Rule result** blade describes the selected issue and proposes mitigation steps. Implement the suggested mitigation steps if you want to configure the selected table for Stretch Database.

## Next step
 Enable Stretch Database.

-   To enable Stretch Database on a **database**, see [Enable Stretch Database for a database](assetId:///37854256-8c99-4566-a552-432e3ea7c6da).

-   To enable Stretch Database on another **table**, when Stretch is already enabled on the database, see [Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc).

## See Also
 [Surface area limitations and blocking issues for Stretch Database](assetId:///2b1fbec1-7859-44fc-8417-724fc57a59c0) 
 [Enable Stretch Database for a database](assetId:///37854256-8c99-4566-a552-432e3ea7c6da) 
 [Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc)

  