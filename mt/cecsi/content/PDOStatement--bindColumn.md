---
title: PDOStatement::bindColumn
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
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
# PDOStatement::bindColumn
Binds a variable to a column in a result set.  
  
## Syntax  
  
```  
  
bool PDOStatement::bindColumn($column, &$param[, $type[, $maxLen[, $driverdata ]]] );  
```  
  
#### Parameters  
$*column*: The \(mixed\) number of the column \(1\-based index\) or name of the column in the result set.  
  
&$*param*: The \(mixed\) name of the PHP variable to which the column will be bound.  
  
$*type*: The optional data type of the parameter, represented by a PDO::PARAM\_\* constant.  
  
$*maxLen*: Optional integer, not used by the Microsoft Drivers for PHP for SQL Server.  
  
$*driverdata*: Optional mixed parameter\(s\) for the driver. For example, you could specify PDO::SQLSRV\_ENCODING\_UTF8 to bind the column to a variable as a string encoded in UTF\-8.  
  
## Return Value  
TRUE if success, otherwise FALSE.  
  
## Remarks  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
This example shows how a variable can be bound to a column in a result set.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "SELECT Title, FirstName, EmailAddress FROM Person.Contact where LastName = 'Estes'";  
$stmt = $conn->prepare($query);  
$stmt->execute();  
  
$stmt->bindColumn('EmailAddress', $email);  
while ( $row = $stmt->fetch( PDO::FETCH_BOUND ) ){  
   echo "$email\n";  
}  
?>  
```  
  
## See Also  
[PDOStatement Class](../content/PDOStatement-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
