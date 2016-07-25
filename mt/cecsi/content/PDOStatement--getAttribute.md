---
title: "PDOStatement::getAttribute"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
caps.latest.revision: 10
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
# PDOStatement::getAttribute
Retrieves the value of a predefined PDOStatement attribute or custom driver attribute.  
  
## Syntax  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### Parameters  
$*attribute*: An integer, one of the PDO::ATTR_* or PDO::SQLSRV_ATTR_\* constants. Supported attributes are the attributes you can set with [PDOStatement::setAttribute](../Topic/PDOStatement::setAttribute.md), PDO::SQLSRV_ATTR_DIRECT_QUERY (see [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../content/Direct-Statement-Execution-and-Prepared-Statement-Execution-in-the-PDO_SQLSRV-Driver.md) for more information about PDO::SQLSRV_ATTR_DIRECT_QUERY), and PDO::ATTR_CURSOR.  
  
## Return Value  
On success, returns a (mixed) value for a predefined PDO attribute or custom driver attribute. Returns null on failure.  
  
## Remarks  
See [PDOStatement::setAttribute](../Topic/PDOStatement::setAttribute.md) for a sample.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## See Also  
[PDOStatement Class](../content/PDOStatement-Class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
