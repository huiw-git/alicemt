---
title: "Use XML Data in Applications"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Use XML Data in Applications
This topic describes the options that are available to you for working with the **xml** data type in your application. The topic includes information about the following:  
  
-   Handling XML from an **xml** type column by using ADO and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Native Client  
  
-   Handling XML from an **xml** type column by using ADO.NET  
  
-   Handling **xml** type in parameters by using ADO.NET  
  
## Handling XML from an xml Type Column by Using ADO and SQL Server Native Client  
 To use MDAC components to access the types and features that were introduced in [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], you must set the **DataTypeCompatibility** initialization property in the ADO connection string.  
  
 For example, the following Visual Basic Scripting Edition (VBScript) sample shows the results of querying an **xml** data type column, `Demographics`, in the `Sales.Store` table of the `AdventureWorks2012` sample database. Specifically, the query looks for the instance value of this column for the row where the `CustomerID` is equal to `3`.  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 This example shows how to set the data type compatibility property. By default, this is set to 0 when you are using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Native Client. If you set the value to 80, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Native Client provider will make **xml** and user-defined type columns appear as [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/tokens/ssVersion2000_md.md)] data types. This would be DBTYPE_WSTR and DBTYPE_BYTES, respectively.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Native Client must also be installed on the client computer and the connection string must specify it for use as the data provider with "`Provider=SQLNCLI11;...`".  
  
#### To test this example  
  
1.  Verify that the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Native Client is installed and that MDAC 2.6.0or later is available on the client computer.  
  
     For more information, see [Implementing XML in SQL Server](assetId:///14ba2cb1-a424-4e4d-b224-0bf1015ab801).  
  
2.  Verify that the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] sample database in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is installed.  
  
     This example requires the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] sample database.  
  
3.  Copy the code shown previously in this topic and paste the code into your text or code editor. Save the file as HandlingXmlDataType.vbs.  
  
4.  Modify the script as required for your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installation and save your changes.  
  
     For example, where `MyServer` is specified, you should replace it with either `(local)` or the actual name of the server on which [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is installed.  
  
5.  Run HandlingXmlDataType.vbs and execute the script.  
  
 The results should be similar to the following sample output:  
  
```  
Row 1  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>1500000</AnnualSales>  
  <AnnualRevenue>150000</AnnualRevenue>  
  <BankName>Primary International</BankName>  
  <BusinessType>OS</BusinessType>  
  <YearOpened>1974</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>38000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>40</NumberEmployees>  
</StoreSurvey>  
  
Row 2  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## Handling XML from an xml Type Column by Using ADO.NET  
 To handle XML from an **xml** data type column by using ADO.NET and the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] you can use the standard behavior of the **SqlCommand** class. For example, an **xml** data type column and its values can be retrieved in the same way any SQL column is retrieved by using a **SqlDataReader**.However, if you want to work with the contents of an **xml** data type column as XML, you will first have to assign the contents to an **XmlReader** type.  
  
 For more information and example code, see "XML Column Values in a Data Reader" in the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnlong](../../Topics/TopicNameNotContainA/tokens/dnprdnlong_md.md)] SDK documentation.  
  
## Handling an xml Type Column in Parameters by Using ADO.NET  
 To handle an xml data type passed as a parameter in ADO.NET and the [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)], you can supply the value as an instance of the **SqlXml** data type. No special handling is involved, because **xml** data type columns in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can accept parameter values in the same way as other columns and data types, such as **string** or **integer**.  
  
 For more information and example code, see "XML Values as Command Parameters" in the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnlong](../../Topics/TopicNameNotContainA/tokens/dnprdnlong_md.md)] SDK documentation.  
  
## See Also  
 [XML Data (SQL Server)](../../Topics/TopicNameNotContainA/XML-Data--SQL-Server-.md)