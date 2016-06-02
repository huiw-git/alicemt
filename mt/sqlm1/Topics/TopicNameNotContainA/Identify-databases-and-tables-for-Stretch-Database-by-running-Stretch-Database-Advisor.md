---
title: Identify databases and tables for Stretch Database by running Stretch Database Advisor
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81bd93d8-eef8-4572-88d7-5c37ab5ac2bf
---
# Identify databases and tables for Stretch Database by running Stretch Database Advisor
  To identify databases and tables that are candidates for Stretch Database, download SQL Server 2016 Upgrade Advisor and run the Stretch Database Advisor. Stretch Database Advisor also identifies blocking issues.  
  
## Download and install Upgrade Advisor  
 Download and install Upgrade Advisor from [here](http://go.microsoft.com/fwlink/?LinkID=613421). This tool is not included on the [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] installation media.  
  
## Run the Stretch Database Advisor  
  
1.  Run Upgrade Advisor.  
  
2.  Select **Scenarios**, and then select **RUN STRETCH DATABASE ADVISOR**.  
  
3.  On the **Run Stretch Database Advisor** blade, click **SELECT DATABASES TO ANALYZE**.  
  
4.  On the **Select databases** blade, click **SQL INSTANCE**.  
  
5.  On the **Connect to SQL Instance** blade, enter the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. Then click **Connect**.  
  
6.  On the **Select databases** blade, select the databases to analyze. Then click **Select**.  
  
7.  On the **Run Stretch Database Advisor** blade, click **Run**.  The analysis runs.  
  
## Review the results  
  
1.  When the analysis is finished, on the **Stretch Database Advisor** blade, select one of the databases that you analyzed to display the **Analysis results** blade.  
  
     The **Analysis results** blade lists recommended tables in the selected database that match the default recommendation criteria. Optionally, adjust the  minimum size and row count to expand or shrink the list of recommended tables.  
  
2.  In the list of recommended tables on the **Analysis results** blade, select one of the recommended tables to display the **Table results** blade.  
  
     The **Table results** blade lists the blocking issues for the selected table. For information about blocking issues detected by Stretch Database Advisor, see [Limitations for Stretch Database](../../Topics\TopicNameNotContainA/Limitations-for-Stretch-Database.md).  
  
3.  In the list of blocking issues on the **Table results** blade, select one of the issues to display the **Rule result** blade.  
  
     The **Rule result** blade describes the selected issue and proposes mitigation steps. Implement the suggested mitigation steps if you want to configure the selected table for Stretch Database.  
  
## Next step  
 Enable Stretch Database.  
  
-   To enable Stretch Database on a **database**, see [Enable Stretch Database for a database](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-database.md).  
  
-   To enable Stretch Database on another **table**, when Stretch is already enabled on the database, see [Enable Stretch Database for a table](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-table.md).  
  
## See Also  
 [Limitations for Stretch Database](../../Topics\TopicNameNotContainA/Limitations-for-Stretch-Database.md)   
 [Enable Stretch Database for a database](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-database.md)   
 [Enable Stretch Database for a table](../../Topics\TopicNameContainA/Enable-Stretch-Database-for-a-table.md)  
  
  