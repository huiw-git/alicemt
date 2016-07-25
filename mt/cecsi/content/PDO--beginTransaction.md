---
title: "PDO::beginTransaction"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
caps.latest.revision: 10
manager: jhubbard
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
# PDO::beginTransaction
Turns off auto commit mode and begins a transaction.  
  
## Syntax  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## Return Value  
true if the method call succeeded, false otherwise.  
  
## Remarks  
The transaction begun with PDO::beginTransaction will end when [PDO::commit](../Topic/PDO::commit.md) or [PDO::rollback](../Topic/PDO::rollback.md) is called.  
  
PDO::beginTransaction is not affected by (and does not affect) the value of PDO::ATTR_AUTOCOMMIT.  
  
You are not allowed to call PDO::beginTransaction before the previous PDO::beginTransaction is ended with PDO::rollback or PDO::commit.  
  
The connection will return to auto commit mode if this method fails.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
The following example uses a database called Test and a table called Table1. It starts a transaction and then issues commands to add two rows and then delete one row. The commands are sent to the database and the transaction is explicitly ended with `PDO::commit`.  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## See Also  
[PDO Class](../content/PDO-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
