---
title: "Creating Test Cases (SybaseToSQL)"
ms.custom: na
ms.date: 07/18/2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
caps.latest.revision: 5
manager: lonnyb
---
# Creating Test Cases (SybaseToSQL)
Use the Test Case Wizard to create a test. This wizard lets you create test cases by choosing tested and verified objects and by specifying the testing parameters.  
  
## Starting the Test Case Wizard  
To start the Test Case Wizard click **New Test Case…** from the **Tester** menu.  
  
When started, the wizard looks for database ssmatester2005db or ssmatester2008db (depending on the project type) on the source Sybase server. It is the Tester extension schema used for storing auxiliary objects. If the Test Case Wizard cannot find ssmatester2005db or ssmatester2008db, it displays a dialog window that proposes to create the Tester extension database. (That situation usually happens during the first run of SSMA Tester.)  
  
If you get the dialog window, click **Yes** to create Sybase tester database on the source server. Then a new dialog window will appear where you should add one or more devices on which to locate new Tester database. Click **Add** to add a device. In the **Allocation Space for Tester Database** dialog choose the device and specify the size used by tester database. Additionally, you can set the separate device for database logs. Note that you must have Sybase privileges to create databases.  
  
## Overview of Creating Test Cases Using the Wizard  
The process of creating a test case consists of five steps:  
  
1.  [Initializing Test Cases &#40;SybaseToSQL&#41;](../content/Initializing-Test-Cases--SybaseToSQL-.md).  
  
2.  [Selecting and Configuring Objects to Test &#40;SybaseToSQL&#41;](../content/Selecting-and-Configuring-Objects-to-Test--SybaseToSQL-.md).  
  
3.  [Selecting and Configuring Affected Objects &#40;SybaseToSQL&#41;](../content/Selecting-and-Configuring-Affected-Objects--SybaseToSQL-.md).  
  
4.  [Customizing Calls Order &#40;SybaseToSQL&#41;](../content/Customizing-Calls-Order--SybaseToSQL-.md).  
  
5.  [Finishing Test Case Preparation &#40;SybaseToSQL&#41;](../content/Finishing-Test-Case-Preparation--SybaseToSQL-.md).  
  
## See Also  
[Testing Migrated Database Objects &#40;SybaseToSQL&#41;](../content/Testing-Migrated-Database-Objects--SybaseToSQL-.md)  
  
