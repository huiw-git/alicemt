---
title: Cursor Types (PDO_SQLSRV Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
manager:jhubbard
---
# Cursor Types (PDO_SQLSRV Driver)
The PDO\_SQLSRV driver lets you create scrollable result sets with one of several cursors.  
  
For information on how to specify a cursor using the PDO\_SQLSRV driver, and for code samples, see [PDO::prepare](../Topic/PDO::prepare.md).  
  
## PDO\_SQLSRV and Server\-Side Cursors  
Prior to version 3.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], the PDO\_SQLSRV driver allowed you to create a result set with a server\-side forward\-only or static cursor. Beginning in version 3.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], keyset and dynamic cursors are also available.  
  
You can indicate the type of server\-side cursor by using PDO::prepare or PDOStatement::setAttribute to select either cursor type:  
  
-   PDO::ATTR\_CURSOR \=> PDO::CURSOR\_FWDONLY  
  
-   PDO::ATTR\_CURSOR \=> PDO::CURSOR\_SCROLL  
  
You can request a keyset or dynamic cursor by specifying PDO::ATTR\_CURSOR \=> PDO::CURSOR\_SCROLL and then pass the appropriate value to PDO::SQLSRV\_ATTR\_CURSOR\_SCROLL\_TYPE. Possible values that you can pass to PDO::SQLSRV\_ATTR\_CURSOR\_SCROLL\_TYPE are:  
  
-   PDO::SQLSRV\_CURSOR\_BUFFERED  
  
-   PDO::SQLSRV\_CURSOR\_DYNAMIC  
  
-   PDO::SQLSRV\_CURSOR\_KEYSET\_DRIVEN  
  
-   PDO::SQLSRV\_CURSOR\_STATIC  
  
## PDO\_SQLSRV and Client\-Side Cursors  
Client\-side cursors were added in version 3.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] that allows you to cache an entire result set in memory. One advantage is that row count is available after a query is executed.  
  
Client\-side cursors should be used for small\- to medium\-sized result sets. Large result sets should use server\-side cursors.  
  
A query will return false if the buffer is not large enough to hold an entire result set when using a client\-side cursor. You can increase the buffer size up to the PHP memory limit.  
  
You can configure the size of the buffer that holds the result set with the PDO::SQLSRV\_ATTR\_CLIENT\_BUFFER\_MAX\_KB\_SIZE attribute of [PDO::setAttribute](../Topic/PDO::setAttribute.md) or [PDOStatement::setAttribute](../Topic/PDOStatement::setAttribute.md). You can also set the maximum buffer size in the php.ini file with pdo\_sqlsrv.client\_buffer\_max\_kb\_size \(for example, pdo\_sqlsrv.client\_buffer\_max\_kb\_size \= 1024\).  
  
You indicate that you want a client\-side cursor by using PDO::prepare or PDOStatement::setAttribute and select the PDO::ATTR\_CURSOR \=> PDO::CURSOR\_SCROLL cursor type.  You then specify PDO::SQLSRV\_ATTR\_CURSOR\_SCROLL\_TYPE \=> PDO::SQLSRV\_CURSOR\_BUFFERED.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED));  
$stmt->execute();  
print $stmt->rowCount();  
  
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
[Specifying a Cursor Type and Selecting Rows](../content/Specifying-a-Cursor-Type-and-Selecting-Rows.md)  
  
