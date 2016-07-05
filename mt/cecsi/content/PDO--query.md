---
title: PDO::query
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6f5e6d4-8ca9-4f06-89ed-de65ad3952a2
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
# PDO::query
Executes an SQL query and returns a result set as a PDOStatement object.  
  
## Syntax  
  
```  
  
PDOStatement PDO::query ($statement[, $fetch_style);  
```  
  
#### Parameters  
*$statement*: The SQL statement you want to execute.  
  
*$fetch\_style*: The optional instructions on how to perform the query. See the Remarks section for more details. $*fetch\_style* in PDO::query can be overridden with $*fetch\_style* in PDO::fetch.  
  
## Return Value  
If the call succeeds, PDO::query returns a PDOStatement object. If the call fails, PDO::query throws a PDOException object or returns false, depending on the setting of PDO::ATTR\_ERRMODE.  
  
## Exceptions  
PDOException.  
  
## Remarks  
A query executed with PDO::query can execute either a prepared statement or directly, depending on the setting of PDO::SQLSRV\_ATTR\_DIRECT\_QUERY; see [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../content/Direct-Statement-Execution-and-Prepared-Statement-Execution-in-the-PDO_SQLSRV-Driver.md) for more information.  
  
PDO::SQLSRV\_ATTR\_QUERY\_TIMEOUT also affects the behavior of PDO::exec; see [PDO::setAttribute](../Topic/PDO::setAttribute.md) for more information.  
  
You can specify the following options for $*fetch\_style*.  
  
|Style|Description|  
|---------|---------------|  
|PDO::FETCH\_COLUMN, *num*|Queries for data in the specified column. The first column in the table is column 0.|  
|PDO::FETCH\_CLASS, '*classname*', array\( *arglist* \)|Creates an instance of a class and assigns column names to properties in the class. If the class constructor takes one or more parameters, you can also pass an *arglist*.|  
|PDO::FETCH\_CLASS, '*classname*'|Assigns column names to properties in an existing class.|  
  
Call PDOStatement::closeCursor to release database resources associated with the PDOStatement object before calling PDO::query again.  
  
You can close a PDOStatement object by setting it to null.  
  
If all the data in a result set is not fetched, the next PDO::query call will not fail.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
This example shows several queries.  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
$conn->setAttribute( PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 1 );  
  
$query = 'select * from Person.ContactType';  
  
// simple query  
$stmt = $conn->query( $query );  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print_r( $row['Name'] ."\n" );  
}  
  
echo "\n........ query for a column ............\n";  
  
// query for one column  
$stmt = $conn->query( $query, PDO::FETCH_COLUMN, 1 );  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query with a new class ............\n";  
$query = 'select * from HumanResources.Department order by GroupName';  
// query with a class  
class cc {  
   function __construct( $arg ) {  
      echo "$arg";  
   }  
  
   function __toString() {  
      return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
   }  
}  
  
$stmt = $conn->query( $query, PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query into an existing class ............\n";  
$c_obj = new cc( '' );  
$stmt = $conn->query( $query, PDO::FETCH_INTO, $c_obj );  
while ( $stmt->fetch() ){  
   echo "$c_obj\n";  
}  
  
$stmt = null;  
?>  
```  
  
## See Also  
[PDO Class](../content/PDO-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
