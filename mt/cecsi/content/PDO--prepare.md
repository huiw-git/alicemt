---
title: PDO::prepare
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
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
# PDO::prepare
Prepares a statement for execution.  
  
## Syntax  
  
```  
  
PDOStatement PDO::prepare ( $statement [, array(key_pair)] )  
```  
  
#### Parameters  
$*statement*: A string containing the SQL statement.  
  
*key\_pair*: An array containing an attribute name and value. See the Remarks section for more information.  
  
## Return Value  
Returns a PDOStatement object on success. On failure, returns a PDOException object, or false depending on the value of PDO::ATTR\_ERRMODE.  
  
## Remarks  
The [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] does not evaluate prepared statements until execution.  
  
The following table lists the possible *key\_pair* values.  
  
|Key|Description|  
|-------|---------------|  
|PDO::ATTR\_CURSOR|Specifies cursor behavior. The default is PDO::CURSOR\_FWDONLY. PDO::CURSOR\_SCROLL is a static cursor.<br /><br />For example, `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />If you use PDO::CURSOR\_SCROLL, you can use PDO::SQLSRV\_ATTR\_CURSOR\_SCROLL\_TYPE, which is described below.<br /><br />See [Cursor Types &#40;PDO_SQLSRV Driver&#41;](../content/Cursor-Types--PDO_SQLSRV-Driver-.md) for more information about result sets and cursors in the PDO\_SQLSRV driver.|  
|PDO::ATTR\_EMULATE\_PREPARES|The purpose of PDO::ATTR\_EMULATE\_PREPARES is described in the [PHP manual](http://us3.php.net/pdo).<br /><br />[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] does not support named or positional parameters in some [!INCLUDE[tsql](../content/includes/tsql_md.md)] clauses.<br /><br />If your PHP application must use parameters in a [!INCLUDE[tsql](../content/includes/tsql_md.md)] clause that will generate an error on the server, you can set the PDO::ATTR\_EMULATE\_PREPARES attribute to true. For example:<br /><br />`PDO::ATTR_EMULATE_PREPARES => true`<br /><br />By default, this attribute is set to false.<br /><br />**Note:** The security of parameterized queries is not in effect when you use `PDO::ATTR_EMULATE_PREPARES => true`. Your application should ensure that the data that is bound to the parameter\(s\) does not contain malicious [!INCLUDE[tsql](../content/includes/tsql_md.md)] code.|  
|PDO::SQLSRV\_ATTR\_ENCODING|PDO::SQLSRV\_ENCODING\_UTF8 \(default\)<br /><br />PDO::SQLSRV\_ENCODING\_SYSTEM<br /><br />PDO::SQLSRV\_ENCODING\_BINARY|  
|PDO::SQLSRV\_ATTR\_DIRECT\_QUERY|When True, specifies direct query execution. False means prepared statement execution. For more information about PDO::SQLSRV\_ATTR\_DIRECT\_QUERY, see [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../content/Direct-Statement-Execution-and-Prepared-Statement-Execution-in-the-PDO_SQLSRV-Driver.md).|  
|PDO::SQLSRV\_ATTR\_QUERY\_TIMEOUT|For more information, see [PDO::setAttribute](../Topic/PDO::setAttribute.md).|  
  
When you use PDO::ATTR\_CURSOR \=> PDO::CURSOR\_SCROLL, you can use PDO::SQLSRV\_ATTR\_CURSOR\_SCROLL\_TYPE. For example,  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
The following table shows the possible values for PDO::SQLSRV\_ATTR\_CURSOR\_SCROLL\_TYPE.  
  
|Value|Description|  
|---------|---------------|  
|PDO::SQLSRV\_CURSOR\_BUFFERED|Creates a client\-side \(buffered\) static cursor. For more information about client\-side cursors, see [Cursor Types &#40;PDO_SQLSRV Driver&#41;](../content/Cursor-Types--PDO_SQLSRV-Driver-.md).|  
|PDO::SQLSRV\_CURSOR\_DYNAMIC|Creates a server\-side \(unbuffered\) dynamic cursor, which lets you access rows in any order and will reflect changes in the database.|  
|PDO::SQLSRV\_CURSOR\_KEYSET\_DRIVEN|Creates a server\-side keyset cursor. A keyset cursor does not update the row count if a row is deleted from the table \(a deleted row is returned with no values\).|  
|PDO::SQLSRV\_CURSOR\_STATIC|Creates a server\-side static cursor, which lets you access rows in any order but will not reflect changes in the database.<br /><br />PDO::ATTR\_CURSOR \=> PDO::CURSOR\_SCROLL implies PDO::SQLSRV\_ATTR\_CURSOR\_SCROLL\_TYPE \=> PDO::SQLSRV\_CURSOR\_STATIC.|  
  
You can close a PDOStatement object by setting it to null.  
  
## Example  
This example shows how to use the PDO::prepare method with parameter markers and a forward\-only cursor.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table1(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
echo "\n";  
  
$query = "insert into Table1(col1, col2) values(:col1, :col2)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( ':col1' => $col1, ':col2' => $col2 ) );  
print $stmt->rowCount();  
  
$stmt = null  
?>  
```  
  
## Example  
This example shows how to use the PDO::prepare method with a client\-side cursor. For a sample showing a server\-side cursor, see [Cursor Types &#40;PDO_SQLSRV Driver&#41;](../content/Cursor-Types--PDO_SQLSRV-Driver-.md).  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  
  
## See Also  
[PDO Class](../content/PDO-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
