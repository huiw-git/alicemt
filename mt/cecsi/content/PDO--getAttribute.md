---
title: PDO::getAttribute
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c81833ea-8b8a-459d-8f24-920098da994d
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
# PDO::getAttribute
Retrieves the value of a predefined PDO or driver attribute.  
  
## Syntax  
  
```  
  
mixed PDO::getAttribute ( $attribute )  
```  
  
#### Parameters  
*$attribute*: One of the supported attributes. See the Remarks section for the list of supported attributes.  
  
## Return Value  
On success, returns the value of a connection option, predefined PDO attribute, or custom driver attribute. On failure, returns null.  
  
## Remarks  
The following table contains the list of supported attributes.  
  
|Attribute|Processed by|Supported Values|Description|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR\_CASE|PDO|PDO::CASE\_LOWER<br /><br />PDO::CASE\_NATURAL<br /><br />PDO::CASE\_UPPER|Specifies whether the column names should be in a specific case. PDO::CASE\_LOWER forces lower case column names, PDO::CASE\_NATURAL leaves the column name as returned by the database, and PDO::CASE\_UPPER forces column names to upper case.<br /><br />The default is PDO::CASE\_NATURAL.<br /><br />This attribute can also be set using PDO::setAttribute.|  
|PDO::ATTR\_CLIENT\_VERSION|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|Array of strings|Describes the versions of the driver and related libraries. Returns an array with the following elements: ODBC version \(*MajorVer*.*MinorVer*\), [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client DLL name and version, [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version \(*MajorVer*.*MinorVer*.*BuildNumber*.*Revision*\)|  
|PDO::ATTR\_DEFAULT\_FETCH\_MODE|PDO|See the PDO documentation.|See the PDO documentation.|  
|PDO::ATTR\_DRIVER\_NAME|PDO|String|Always returns "sqlsrv".|  
|PDO::ATTR\_DRIVER\_VERSION|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|String|Indicates the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version \(*MajorVer*.*MinorVer*.*BuildNumber*.*Revision*\)|  
|PDO::ATTR\_ERRMODE|PDO|PDO::ERRMODE\_SILENT<br /><br />PDO::ERRMODE\_WARNING<br /><br />PDO::ERRMODE\_EXCEPTION|Specifies how failures should be handled by the driver.<br /><br />PDO::ERRMODE\_SILENT \(the default\) sets the error codes and information.<br /><br />PDO::ERRMODE\_WARNING raises an E\_WARNING.<br /><br />PDO::ERRMODE\_EXCEPTION raises an exception.<br /><br />This attribute can also be set using PDO::setAttribute.|  
|PDO::ATTR\_ORACLE\_NULLS|PDO|See the PDO documentation.|See the PDO documentation.|  
|PDO::ATTR\_SERVER\_INFO|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|Array of 3 elements|Returns the current database, SQL Server version, and SQL Server instance.|  
|PDO::ATTR\_SERVER\_VERSION|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|String|Indicates the SQL Server version \(*Major*.*Minor*.*BuildNumber*\)|  
|PDO::ATTR\_STATEMENT\_CLASS|PDO|See PDO documentation|See PDO documentation. \(returns PDOStatement\)|  
|PDO::ATTR\_STRINGIFY\_FETCHES|PDO|See PDO documentation|See the PDO documentation.|  
|PDO::SQLSRV\_ATTR\_CLIENT\_BUFFER\_MAX\_KB\_SIZE|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|1 to the PHP memory limit.|Configures the size of the buffer that holds the result set for a client\-side cursor.<br /><br />The default is 10240 KB \(10 MB\).<br /><br />For more information about client\-side cursors, see [Cursor Types &#40;SQLSRV Driver&#41;](../content/Cursor-Types--SQLSRV-Driver-.md).|  
|PDO::SQLSRV\_ATTR\_DIRECT\_QUERY|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|true<br /><br />false|Specifies direct or prepared query execution. For more information, see [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../content/Direct-Statement-Execution-and-Prepared-Statement-Execution-in-the-PDO_SQLSRV-Driver.md).|  
|PDO::SQLSRV\_ATTR\_ENCODING|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|One of the following:<br /><br />PDO::SQLSRV\_ENCODING\_UTF8<br /><br />PDO::SQLSRV\_ENCODING\_SYSTEM|Specifies the character set encoding used by the driver to communicate with the server.<br /><br />The default is PDO::SQLSRV\_ENCODING\_UTF8.|  
  
PDO processes some of the predefined attributes while it requires the driver to handle others. All custom attributes and connection options are handled by the driver, an unsupported attribute or connection option will return null.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
This example shows the value of the PDO::ATTR\_ERRMODE attribute, before and after changing its value.  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
  
$attributes1 = array( "ERRMODE" );  
foreach ( $attributes1 as $val ) {  
     echo "PDO::ATTR_$val: ";  
     var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
}  
  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
  
$attributes1 = array( "ERRMODE" );  
foreach ( $attributes1 as $val ) {  
     echo "PDO::ATTR_$val: ";  
     var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
}  
  
// An example using PDO::ATTR_CLIENT_VERSION  
print_r($conn->getAttribute( PDO::ATTR_CLIENT_VERSION ));  
?>  
```  
  
## See Also  
[PDO Class](../content/PDO-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
