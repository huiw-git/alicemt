---
title: Compare Replicated Tables for Differences (Replication Programming)
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
---
# Compare Replicated Tables for Differences (Replication Programming)
  Article validation is used to determine if published data for table articles at the Publisher and Subscriber are not identical, which can indicate non\-convergence. For more information, see [Validate Replicated Data](../../Topics\TopicNameNotContainA/Validate-Replicated-Data.md). However, validation only returns pass or fail information and does not provide any information about what is different between the source and destination tables. The **tablediff** command prompt utility returns detailed difference information between two tables and can even generate a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script to bring a subscription into convergence with data at the Publisher.  
  
> [!NOTE]  
>  The **tablediff** utility is only supported for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] servers.  
  
### To compare replicated tables for differences using tablediff  
  
1.  From the command prompt at any server in a replication topology, run the [tablediff Utility](../../Topics\TopicNameNotContainA/tablediff-Utility.md). Specify the following parameters:  
  
    -   **\-sourceserver** \- name of the server on which the data is known to be correct, usually the Publisher.  
  
    -   **\-sourcedatabase** \- name of the database containing the correct data.  
  
    -   **\-sourcetable** \- name of the source table for the article being compared.  
  
    -   \(Optional\) **\-sourceschema** \- schema owner of the source table, if not the default schema.  
  
    -   \(Optional\) **\-sourceuser** and **\-sourcepassword** when using SQL Server Authentication to connect to the Publisher.  
  
        > [!IMPORTANT]  
        >  When possible, use Windows Authentication. If you must use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, prompt users to enter security credentials at runtime. If you must store credentials in a script file, you must secure the file to prevent unauthorized access.  
  
    -   **\-destinationserver** \- name of the server on which the data is being compared, usually a Subscriber.  
  
    -   **\-destinationdatabase** \- name of a the database being compared.  
  
    -   **\-destinationtable** \- name of the table being compared.  
  
    -   \(Optional\) **\-destinationschema** \- schema owner of the destination table, if not the default schema.  
  
    -   \(Optional\) **\-destinationuser** and **\-destinationpassword** when using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication to connect to the Subscriber.  
  
        > [!IMPORTANT]  
        >  When possible, use Windows Authentication. If you must use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, prompt users to enter security credentials at runtime. If you must store credentials in a script file, you must secure the file to prevent unauthorized access.  
  
    -   \(Optional\) Use **\-c** to do a column\-level comparison.  
  
    -   \(Optional\) Use **\-q** to do a fast, row count\- and schema\-only comparison.  
  
    -   \(Optional\) Specify a file name and path for **\-o** to output the results to a file.  
  
    -   \(Optional\) Specify a table in the subscription database into which to insert results for **\-et**. If the table already exists, specify **\-dt** to first drop the table.  
  
    -   \(Optional\) Use **\-f** to generate a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] file to fix data at the Subscriber so that it matches data at the Publisher. Use **\-df** to specify the number of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements in each file.  
  
    -   \(Optional\) Use **\-rc** and **\-ri** to specify the number of times to retry an operation and the retry interval.  
  
    -   \(Optional\) Use **\-strict** to enforce strict schema comparison between source and destination tables.  
  
## See Also  
 [Validate Data at the Subscriber](../../Topics\TopicNameNotContainA/Validate-Data-at-the-Subscriber.md)  
  
  