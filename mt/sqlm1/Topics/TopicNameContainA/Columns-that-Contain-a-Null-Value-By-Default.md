---
title: Columns that Contain a Null Value By Default
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
---
# Columns that Contain a Null Value By Default
  By default, a null value in a column maps to the absence of the attribute, node, or element. This default behavior can be overwritten by requesting element\-centric XML using the ELEMENTS directive and specifying XSINIL to request adding elements for NULL values, as shown in the following query:  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 The following shows the result. Note that if XSINIL is not specified, the \<`Middle`\> element will be absent.  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## See Also  
 [Use PATH Mode with FOR XML](../../Topics\TopicNameNotContainA/Use-PATH-Mode-with-FOR-XML.md)  
  
  