---
title: PDO::errorCode
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
manager:jhubbard
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
# PDO::errorCode
PDO::errorCode retrieves the SQLSTATE of the most recent operation on the database handle.  
  
## Syntax  
  
```  
  
mixed PDO::errorCode();  
```  
  
## Return Value  
PDO::errorCode returns a five\-char SQLSTATE as a string or NULL if there was no operation on the database handle.  
  
## Remarks  
PDO::errorCode in the PDO\_SQLSRV driver will return warnings on some successful operations. For example, on a successful connection, PDO::errorCode will return "01000" indicating SQL\_SUCCESS\_WITH\_INFO.  
  
PDO::errorCode only retrieves error codes for operations performed directly on the database connection. If you create a PDOStatement instance through PDO::prepare or PDO::query and generate an error on the statement object, PDO::errorCode will not retrieve that error. You must call PDOStatement::errorCode to return the error code for an operation performed on a particular statement object.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
In this example, the name of the column is misspelled \(`Cityx` instead of `City`\), causing an error, which is then reported.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## See Also  
[PDO Class](../content/PDO-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
