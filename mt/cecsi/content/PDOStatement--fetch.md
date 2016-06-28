---
title: PDOStatement::fetch
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4368e362-5bda-4da1-8462-33714683c39f
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
# PDOStatement::fetch
Retrieves a row from a result set.  
  
## Syntax  
  
```  
  
mixed PDOStatement::fetch ([ $fetch_style[, $cursor_orientation[, $cursor_offset]]] );  
```  
  
#### Parameters  
$*fetch\_style*: An optional \(integer\) symbol specifying the format of the row data. See the Remarks section for the list of possible values for $*fetch\_style*. Default is PDO::FETCH\_BOTH. $*fetch\_style* in the fetch method will override the $*fetch\_style* specified in the PDO::query method.  
  
$*cursor\_orientation*: An optional \(integer\) symbol indicating the row to retrieve when the prepare statement specifies `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`. See the Remarks section for the list of possible values for $*cursor\_orientation*. See [PDO::prepare](../Topic/PDO::prepare.md) for a sample using a scrollable cursor.  
  
$*cursor\_offset*: An optional \(integer\) symbol specifying the row to fetch when $*cursor\_orientation* is either PDO::FETCH\_ORI\_ABS or PDO::FETCH\_ORI\_REL and PDO::ATTR\_CURSOR is PDO::CURSOR\_SCROLL.  
  
## Return Value  
A mixed value that returns a row or false.  
  
## Remarks  
The cursor is automatically advanced when fetch is called. The following table contains the list of possible $*fetch\_style* values.  
  
|$*fetch\_style*|Description|  
|-------------------|---------------|  
|PDO::FETCH\_ASSOC|Specifies an array indexed by column name.|  
|PDO::FETCH\_BOTH|Specifies an array indexed by column name and 0\-based order. This is the default.|  
|PDO::FETCH\_BOUND|Returns true and assigns the values as specified by [PDOStatement::bindColumn](../Topic/PDOStatement::bindColumn.md).|  
|PDO::FETCH\_CLASS|Creates an instance and maps columns to named properties.<br /><br />Call [PDOStatement::setFetchMode](../Topic/PDOStatement::setFetchMode.md) before calling fetch.|  
|PDO::FETCH\_INTO|Refreshes an instance of the requested class.<br /><br />Call [PDOStatement::setFetchMode](../Topic/PDOStatement::setFetchMode.md) before calling fetch.|  
|PDO::FETCH\_LAZY|Creates variable names during access and creates an unnamed object.|  
|PDO::FETCH\_NUM|Specifies an array indexed by zero\-based column order.|  
|PDO::FETCH\_OBJ|Specifies an unnamed object with property names that map to column names.|  
  
If the cursor is at the end of the result set \(the last row has been retrieved and the cursor has advanced past the result set boundary\) and if the cursor is forward\-only \(PDO::ATTR\_CURSOR \= PDO::CURSOR\_FWDONLY\), subsequent fetch calls will fail.  
  
If the cursor is scrollable \(PDO::ATTR\_CURSOR \= PDO::CURSOR\_SCROLL\), fetch will move the cursor within the result set boundary. The following table contains the list of possible $*cursor\_orientation* values.  
  
|$*cursor\_orientation*|Description|  
|--------------------------|---------------|  
|PDO::FETCH\_ORI\_NEXT|Retrieves the next row. This is the default.|  
|PDO::FETCH\_ORI\_PRIOR|Retrieves the previous row.|  
|PDO::FETCH\_ORI\_FIRST|Retrieves the first row.|  
|PDO::FETCH\_ORI\_LAST|Retrieves the last row.|  
|PDO::FETCH\_ORI\_ABS, *num*|Retrieves the row requested in $*cursor\_offset* by row number.|  
|PDO::FETCH\_ORI\_REL, *num*|Retrieves the row requested in $*cursor\_offset* by relative position from the current position.|  
  
If the value specified for $*cursor\_offset* or $*cursor\_orientation* results in a position outside result set boundary, fetch will fail.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print( "\n---------- PDO::FETCH_CLASS -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg";  
      }  
  
      function __toString() {  
         return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
      }  
   }  
  
   $stmt->setFetchMode(PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
   while ( $row = $stmt->fetch(PDO::FETCH_CLASS)) {   
      print($row . "\n");   
   }  
  
   print( "\n---------- PDO::FETCH_INTO -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
   $c_obj = new cc( '' );  
  
   $stmt->setFetchMode(PDO::FETCH_INTO, $c_obj);  
   while ( $row = $stmt->fetch(PDO::FETCH_INTO)) {   
      echo "$c_obj\n";  
   }  
  
   print( "\n---------- PDO::FETCH_ASSOC -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_ASSOC );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_NUM -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_NUM );  
   print_r ($result );  
  
   print( "\n---------- PDO::FETCH_BOTH -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_BOTH );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_LAZY -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_LAZY );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_OBJ -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_OBJ );  
   print $result->Name;  
   print( "\n \n" );  
  
   print( "\n---------- PDO::FETCH_BOUND -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->bindColumn('Name', $name);  
   $result = $stmt->fetch( PDO::FETCH_BOUND );  
   print $name;  
   print( "\n \n" );  
?>  
```  
  
## See Also  
[PDOStatement Class](../content/PDOStatement-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
