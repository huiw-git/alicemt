---
title: Specify Data Type Mappings for an Oracle Publisher
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
---
# Specify Data Type Mappings for an Oracle Publisher
  This topic describes how to specify data type mappings for an Oracle Publisher in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. Although a set of default data type mappings are provided for Oracle Publishers, it might be necessary to specify different mappings for a given publication.  
  
 **In This Topic**  
  
-   **To specify data type mappings for an Oracle Publisher, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Specify data type mappings on the **Data Mapping** tab of the **Article Properties \- \<Article\>** dialog box. This is available from the **Articles** page of the New Publication Wizard and the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication from an Oracle Database](../../Topics\TopicNameContainA/Create-a-Publication-from-an-Oracle-Database.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To specify a data type mapping  
  
1.  On the **Articles** page of the New Publication Wizard or the **Publication Properties \- \<Publication\>** dialog box, select a table, and then click **Article Properties**.  
  
2.  Click **Set Properties of Highlighted Table Article**.  
  
3.  On the **Data Mapping** tab of the **Article Properties \- \<Article\>** dialog box, select mappings from the **Subscriber Data Type** column:  
  
    -   For some data types there is only one possible mapping, in which case the column in the property grid is read\-only.  
  
    -   For some types, there is more than one type that you can select. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you use the default mapping unless your application requires a different mapping. For more information, see [Data Type Mapping for Oracle Publishers](../../Topics\TopicNameNotContainA/Data-Type-Mapping-for-Oracle-Publishers.md).  
  
4.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 You can specify custom data type mappings programmatically using replication stored procedures. You can also set the default mappings that are used when mapping data types between [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and a non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database management system \(DBMS\). For more information, see [Data Type Mapping for Oracle Publishers](../../Topics\TopicNameNotContainA/Data-Type-Mapping-for-Oracle-Publishers.md).  
  
#### To define custom data type mappings when creating an article belonging to an Oracle publication  
  
1.  If one does not already exist, create an Oracle publication.  
  
2.  At the Distributor, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). Specify a value of **0** for **@use\_default\_datatypes**. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
3.  At the Distributor, execute [sp\_helparticlecolumns](../Topic/sp_helparticlecolumns%20\(Transact-SQL\).md) to view the existing mapping for a column in a published article.  
  
4.  At the Distributor, execute [sp\_changearticlecolumndatatype](../Topic/sp_changearticlecolumndatatype%20\(Transact-SQL\).md). Specify the name of the Oracle Publisher for **@publisher**, as well as **@publication**, **@article**, and **@column** to define the published column. Specify the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data type to map to for **@type**, as well as **@length**, **@precision**, and **@scale**, where applicable.  
  
5.  At the Distributor, execute [sp\_articleview](../Topic/sp_articleview%20\(Transact-SQL\).md). This creates the view used to generate the snapshot from the Oracle publication.  
  
#### To specify a mapping as the default mapping for a data type  
  
1.  \(Optional\) At the Distributor on any database, execute [sp\_getdefaultdatatypemapping](../Topic/sp_getdefaultdatatypemapping%20\(Transact-SQL\).md). Specify **@source\_dbms**, **@source\_type**, **@destination\_dbms**, **@destination\_version**, and any other parameters needed to identify the source DBMS. Information on the currently mapped data type in the destination DBMS is returned using the output parameters.  
  
2.  \(Optional\) At the Distributor on any database, execute [sp\_helpdatatypemap](../Topic/sp_helpdatatypemap%20\(Transact-SQL\).md). Specify **@source\_dbms** and any other parameters needed to filter the result set. Note the value of **mapping\_id** for the desired mapping in the result set.  
  
3.  At the Distributor on any database, execute [sp\_setdefaultdatatypemapping](../Topic/sp_setdefaultdatatypemapping%20\(Transact-SQL\).md).  
  
    -   If you know the desired value of **mapping\_id** obtained in step 2, specify it for **@mapping\_id**.  
  
    -   If you do not know the **mapping\_id**, specify the parameters **@source\_dbms**, **@source\_type**, **@destination\_dbms**, **@destination\_type**, and any other parameters required to identify an existing mapping.  
  
#### To find valid data types for a given Oracle data type  
  
1.  At the Distributor on any database, execute [sp\_helpdatatypemap](../Topic/sp_helpdatatypemap%20\(Transact-SQL\).md). Specify a value of **ORACLE** for **@source\_dbms** and any other parameters needed to filter the result set.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example changes a column with an Oracle data type of NUMBER so it is mapped to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data type **numeric**\(38,38\), instead of the default data type **float**.  
  
 [!CODE [HowTo#sp_changecolumndatatype](../CodeSnippet/SQL15/replication/howto#sp_changecolumndatatype)]  
  
 This example query returns the default and alternative mappings for the Oracle 9 data type **CHAR**.  
  
 [!CODE [HowTo#sp_helpcolumndatatype_char](../CodeSnippet/SQL15/replication/howto#sp_helpcolumndatatype_char)]  
  
 This example query returns the default mappings for the Oracle 9 data type **NUMBER** when it is specified without a scale or precision.  
  
 [!CODE [HowTo#sp_helpcolumndatatype_number](../CodeSnippet/SQL15/replication/howto#sp_helpcolumndatatype_number)]  
  
## See Also  
 [Data Type Mapping for Oracle Publishers](../../Topics\TopicNameNotContainA/Data-Type-Mapping-for-Oracle-Publishers.md)   
 [Heterogeneous Database Replication](../../Topics\TopicNameNotContainA/Heterogeneous-Database-Replication.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Configure an Oracle Publisher](../../Topics\TopicNameNotContainA/Configure-an-Oracle-Publisher.md)  
  
  