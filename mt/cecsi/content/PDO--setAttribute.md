---
title: PDO::setAttribute
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56f9ee96-e1d2-46cc-b137-38f06a251863
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
# PDO::setAttribute
Sets a predefined PDO attribute or a custom driver attribute.  
  
## Syntax  
  
```  
  
bool PDO::setAttribute ( $attribute, $value );  
```  
  
#### Parameters  
*$attribute*: The attribute to set. See the Remarks section for a list of supported attributes.  
  
*$value*: The value \(type mixed\).  
  
## Return Value  
Returns true on success, otherwise false.  
  
## Remarks  
  
|Attribute|Processed by|Supported values|Description|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR\_CASE|PDO|PDO::CASE\_LOWER<br /><br />PDO::CASE\_NATURAL<br /><br />PDO::CASE\_UPPER|Specifies the case of column names.<br /><br />PDO::CASE\_LOWER causes lower case column names.<br /><br />PDO::CASE\_NATURAL \(the default\) displays column names as returned by the database.<br /><br />PDO::CASE\_UPPER causes column names to upper case.<br /><br />This attribute can be set using PDO::setAttribute.|  
|PDO::ATTR\_DEFAULT\_FETCH\_MODE|PDO|See the PDO documentation.|See the PDO documentation.|  
|PDO::ATTR\_ERRMODE|PDO|PDO::ERRMODE\_SILENT<br /><br />PDO::ERRMODE\_WARNING<br /><br />PDO::ERRMODE\_EXCEPTION|Specifies how the driver will report failures.<br /><br />PDO::ERRMODE\_SILENT \(the default\) sets the error codes and information.<br /><br />PDO::ERRMODE\_WARNING raises E\_WARNING.<br /><br />PDO::ERRMODE\_EXCEPTION causes an exception to be thrown.<br /><br />This attribute can be set using PDO::setAttribute.|  
|PDO::ATTR\_ORACLE\_NULLS|PDO|See the PDO documentation.|Specifies how nulls should be returned.<br /><br />PDO::NULL\_NATURAL does no conversion.<br /><br />PDO::NULL\_EMPTY\_STRING converts an empty string to null.<br /><br />PDO::NULL\_TO\_STRING converts null to an empty string.|  
|PDO::ATTR\_STATEMENT\_CLASS|PDO|See the PDO documentation.|Sets the user\-supplied statement class derived from PDOStatement.<br /><br />Requires `array(string classname, array(mixed constructor_args))`.<br /><br />See the PDO documentation for more information.|  
|PDO::ATTR\_STRINGIFY\_FETCHES|PDO|true or false|Converts numeric values to strings when retrieving data.|  
|PDO::SQLSRV\_ATTR\_CLIENT\_BUFFER\_MAX\_KB\_SIZE|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|1 to the PHP memory limit.|Configures the size of the buffer that holds the result set.<br /><br />The default is 10240 KB \(10 MB\).<br /><br />For more information about queries that create a client\-side cursor, see [Cursor Types &#40;PDO_SQLSRV Driver&#41;](../content/Cursor-Types--PDO_SQLSRV-Driver-.md).|  
|PDO::SQLSRV\_ATTR\_DIRECT\_QUERY|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|true<br /><br />false|Specifies direct or prepared query execution. For more information, see [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../content/Direct-Statement-Execution-and-Prepared-Statement-Execution-in-the-PDO_SQLSRV-Driver.md).|  
|PDO::SQLSRV\_ATTR\_ENCODING|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|PDO::SQLSRV\_ENCODING\_UTF8<br /><br />PDO::SQLSRV\_ENCODING\_SYSTEM.|Sets the character set encoding used by the driver to communicate with the server.<br /><br />PDO::SQLSRV\_ENCODING\_BINARY is not supported.<br /><br />The default is PDO::SQLSRV\_ENCODING\_UTF8.|  
|PDO::SQLSRV\_ATTR\_QUERY\_TIMEOUT|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|integer|Sets the query timeout in seconds.<br /><br />The default is 0, which means the driver will wait indefinitely for results.<br /><br />Negative numbers are not allowed.|  
|PDO::SQLSVR\_CLIENT\_BUFFER\_MAX\_SIZE|[!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]|integer|Sets the size of the query buffer.<br /><br />The default is 0, which indicates unlimited buffer size.<br /><br />Negative numbers are not allowed.<br /><br />For more information about queries that create a client\-side cursor, see [Cursor Types &#40;PDO_SQLSRV Driver&#41;](../content/Cursor-Types--PDO_SQLSRV-Driver-.md).|  
  
PDO processes some of the predefined attributes and requires the driver to process others. All custom attributes and connection options are processed by the driver. An unsupported attribute, connection option, or unsupported value will be reported according to the setting of PDO::ATTR\_ERRMODE.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## Example  
This sample shows how to set the PDO::ATTR\_ERRMODE attribute.  
  
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
?>  
```  
  
## See Also  
[PDO Class](../content/PDO-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
