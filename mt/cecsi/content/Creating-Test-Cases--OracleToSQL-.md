---
title: "Creating Test Cases (OracleToSQL)"
ms.custom: na
ms.date: 07/18/2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
caps.latest.revision: 7
manager: b-tomb
---
# Creating Test Cases (OracleToSQL)
Use the Test Case Wizard to create a test. This wizard lets you create test cases by choosing tested and verified objects and by specifying the testing parameters.  
  
## Starting the Test Case Wizard  
To start the Test Case Wizard click **New Test Case…** from the **Tester** menu.  
  
When started, the wizard looks for schema SSMATESTER_ORACLE on the source Oracle server. It is the Tester extension schema used for storing auxiliary objects. If the Test Case Wizard cannot find SSMATESTER_ORACLE, it displays a dialog window that proposes to create the schema. (That situation usually happens during the first run of SSMA Tester.)  
  
If you get the dialog window, click **Yes** to create SSMATESTER_ORACLE schema on the source server. Note that you must have Oracle privileges to create a new user and create objects in the schema of this user.  
  
## Overview of Creating Test Cases Using the Wizard  
The process of creating a test case consists of five steps:  
  
1.  [Initializing Test Cases &#40;OracleToSQL&#41;](../content/Initializing-Test-Cases--OracleToSQL-.md)  
  
2.  [Selecting and Configuring Objects to Test &#40;OracleToSQL&#41;](../content/Selecting-and-Configuring-Objects-to-Test--OracleToSQL-.md)  
  
3.  [Selecting and Configuring Affected Objects &#40;OracleToSQL&#41;](../content/Selecting-and-Configuring-Affected-Objects--OracleToSQL-.md)  
  
4.  [Customizing Calls Order &#40;OracleToSQL&#41;](../content/Customizing-Calls-Order--OracleToSQL-.md)  
  
5.  [Finishing Test Case Preparation &#40;OracleToSQL&#41;](../content/Finishing-Test-Case-Preparation--OracleToSQL-.md)  
  
## See Also  
[Testing Migrated Database Objects &#40;OracleToSQL&#41;](../content/Testing-Migrated-Database-Objects--OracleToSQL-.md)  
  
