---
title: "PDOStatement::setAttribute"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
caps.latest.revision: 20
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
# PDOStatement::setAttribute
Sets an attribute value, either a predefined PDO attribute or a custom driver attribute.  
  
## Syntax  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### Parameters  
$*attribute*: An integer, one of the PDO::ATTR_* or PDO::SQLSRV_ATTR_\* constants. See the Remarks section for the list of available attributes.  
  
$*value*: The (mixed) value to be set for the specified $*attribute*.  
  
## Return Value  
TRUE on success, FALSE otherwise.  
  
## Remarks  
The following table contains the list of available attributes:  
  
|Attribute|Values|Description|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|1 to the PHP memory limit.|Configures the size of the buffer that holds the result set for a client-side cursor.<br /><br />The default is 10240 KB (10 MB).<br /><br />For more information about client-side cursors, see [Cursor Types &#40;PDO_SQLSRV Driver&#41;](../content/Cursor-Types--PDO_SQLSRV-Driver-.md).|  
|PDO::SQLSRV_ATTR_ENCODING|Integer<br /><br />PDO::SQLSRV_ENCODING_UTF8 (Default)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Sets the character set encoding to be used by the driver to communicate with the server.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Integer|Sets the query timeout in seconds.<br /><br />By default, the driver will wait indefinitely for results. Negative numbers are not allowed.<br /><br />0 means no timeout.|  
  
## Example  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## See Also  
[PDOStatement Class](../content/PDOStatement-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
