---
title: "Alternatives: Using SQL Statements"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
caps.latest.revision: 11
manager: sonalm
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
# Alternatives: Using SQL Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO also allows using commands as alternatives to its built-in properties and methods for editing data. Depending upon your provider, all operations mentioned in this section could also be accomplished by passing commands to your data source. For example, SQL UPDATE statements can be used to modify data without using the <legacyBold>Value</legacyBold> property of a <legacyBold>Field</legacyBold>. SQL INSERT statements can be used to add new records to a data source, rather than the ADO method <legacyBold>AddNew</legacyBold>. For more information about SQL or the data-manipulation language of your provider, see the documentation of your data source.</para>
    <para>For example, you can pass a SQL string containing a DELETE statement to a database, as shown in the following code:</para>
    <code>    'BeginSQLDelete
    strSQL = "DELETE FROM Shippers WHERE ShipperID = " &amp; intId
    objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords
    'EndSQLDelete</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>