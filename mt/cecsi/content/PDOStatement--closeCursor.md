---
title: PDOStatement::closeCursor
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
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
# PDOStatement::closeCursor
Closes the cursor, enabling the statement to be executed again.  
  
## Syntax  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## Return Value  
true on success, otherwise false.  
  
## Remarks  
closeCursor has an effect when the MultipleActiveResultSets connection option is set to false.  For more information about the MultipleActiveResultSets connection option, see [How to: Disable Multiple Active Resultsets \(MARS\)](../Topic/How%20to:%20Disable%20Multiple%20Active%20Resultsets%20(MARS).md).  
  
Instead of calling closeCursor, you can also just set the statement handle to null.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## See Also  
[PDOStatement Class](../content/PDOStatement-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
