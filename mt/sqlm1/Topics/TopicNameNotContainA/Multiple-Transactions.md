---
title: Multiple Transactions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
---
# Multiple Transactions
  It is possible for a package to include unrelated transactions in an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package. Any time a container in the middle of a nested container hierarchy does not support transactions, the containers above or below it in the hierarchy start separate transactions if they are configured to support transactions. The transactions commit or roll back in order from the innermost task in the nested container hierarchy to the package. However, after the inner transaction commits, it does not roll back if an outer transaction is aborted.  
  
## Illustration of Multiple Transactions  
 For example, a package has a Sequence container that holds two Foreach Loop containers, and each container include two Execute SQL tasks. The Sequence container supports transactions, the Foreach Loop containers do not, and the Execute SQL tasks do. In this example, each Execute SQL task would start its own transaction and would not roll back if the transaction on the Sequence task was aborted.  
  
 The TransactionOption properties of the Sequence container, Foreach Loop container and the Execute SQL tasks are set as follows:  
  
-   The TransactionOption property of the Sequence container is set to **Required**.  
  
-   The TransactionOption properties of the Foreach Loop containers are set to **NotSupported**.  
  
-   The TransactionOption properties of the Execute SQL tasks are set to **Required**.  
  
 The following diagram shows the five unrelated transactions in the package. One transaction is started by the Sequence container and four transactions are started by the Execute SQL tasks.  
  
 ![Implementation of multiple transactions](../../Images\Image\ImageNotContaina/MW_DTS_Trans2.gif "MW_DTS_Trans2")  
  
## Related Tasks  
 [Configure a Package to Use Transactions](../../Topics\TopicNameContainA/Configure-a-Package-to-Use-Transactions.md)  
  
  