---
title: Grant a Permission to a Principal
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
---
# Grant a Permission to a Principal
  This topic describes how to grant permission to a principal in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To grant permission to a principal, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 Consider the following best practices that can make managing permissions easier.  
  
-   Grant permission to roles, instead of individual logins or users. When one individual is replaced by another, remove the departing individual from the role and add the new individual to the role. The many permissions that might be associated with the role will automatically be available to the new individual. If several people in an organization require the same permissions, adding each of them to the role will grant them the same permissions.  
  
-   Configure similar securables \(tables, views, and procedures\) to be owned by a schema, then grant permissions to the schema. For example, the payroll schema might own several tables, views, and stored procedures. By granting access to the schema, all the necessary permissions to perform the payroll function can be granted at the same time. For more information about what securables can be granted permissions, see [Securables](../../Topics\TopicNameNotContainA/Securables.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The grantor \(or the principal specified with the AS option\) must have either the permission itself with GRANT OPTION or a higher permission that implies the permission being granted. Members of the **sysadmin** fixed server role can grant any permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To grant permission to a principal  
  
1.  In Object Explorer, expand the database that contains the object to which you want to grant permissions.  
  
    > [!NOTE]  
    >  These steps deal specifically with granting permissions to a stored procedure, but you can use similar steps to add permissions to tables, views, functions, and assemblies, as well as other securables. For more information, see [GRANT &#40;Transact-SQL&#41;](../Topic/GRANT%20\(Transact-SQL\).md)  
  
2.  Expand the **Programmability** folder.  
  
3.  Expand the **Stored Procedures** folder.  
  
4.  Right\-click a stored procedure and select **Properties**.  
  
5.  In the **Stored Procedure Properties –***stored\_procedure\_name* dialog box, under select a page, select **Permissions**. Use this page to add users or roles to the stored procedure and specify the permissions those users or roles have.  
  
6.  When finished, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To grant permission to a principal  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 For more information, see [GRANT &#40;Transact-SQL&#41;](../Topic/GRANT%20\(Transact-SQL\).md) and [GRANT Object Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Object%20Permissions%20\(Transact-SQL\).md).  
  
## See Also  
 [Principals &#40;Database Engine&#41;](../Topic/Principals%20\(Database%20Engine\).md)  
  
  