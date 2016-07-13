---
title: Binding Parameters by Name (Named Parameters)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2c3da5a-6c10-4dd5-acf9-e951eea71a6b
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Binding Parameters by Name (Named Parameters)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Certain DBMSs allow an application to specify the parameters to a stored procedure by name instead of by position in the procedure call. Such parameters are called <legacyItalic>named parameters</legacyItalic>. ODBC supports the use of named parameters. In ODBC, named parameters are used only in calls to stored procedures and cannot be used in other SQL statements.</para>
    <para>The driver checks the value of the SQL_DESC_UNNAMED field of the IPD to determine whether named parameters are used. If SQL_DESC_UNNAMED is not set to SQL_UNNAMED, the driver uses the name in the SQL_DESC_NAME field of the IPD to identify the parameter. To bind the parameter, an application can call <legacyBold>SQLBindParameter</legacyBold> to specify the parameter information and then can call <legacyBold>SQLSetDescField</legacyBold> to set the SQL_DESC_NAME field of the IPD. When named parameters are used, the order of the parameter in the procedure call is not important and the parameter's record number is ignored.</para>
    <para>The difference between unnamed parameters and named parameters is in the relationship between the record number of the descriptor and the parameter number in the procedure. When unnamed parameters are used, the first parameter marker is related to the first record in the parameter descriptor, which in turn is related to the first parameter (in creation order) in the procedure call. When named parameters are used, the first parameter marker is still related to the first record of the parameter descriptor, but the relationship between the record number of the descriptor and the parameter number in the procedure does not exist anymore. Named parameters do not use the mapping of the descriptor record number to the procedure parameter position; instead, the descriptor record name is mapped to the procedure parameter name.</para>
    <alert class="note">
      <para>If automatic population of the IPD is enabled, the driver will populate the descriptor such that the order of the descriptor records will match the order of the parameters in the procedure definition, even if named parameters are used.</para>
    </alert>
    <para>If a named parameter is used, all parameters must be named parameters. If any parameter is not a named parameter, then none of the parameters ca be named parameters. If there were a mixture of named parameters and unnamed parameters, the behavior would be driver-dependent.</para>
    <para>As an example of named parameters, suppose a SQL Server stored procedure has been defined as follows:</para>
    <code>CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS &lt;blah&gt;</code>
    <para>In this procedure, the first parameter, @title_id, has a default value of 1. An application can use the following code to invoke this procedure such that it specifies only one dynamic parameter. This parameter is a named parameter with the name "@quote".</para>
    <code>// Prepare the procedure invocation statement.
SQLPrepare(hstmt, "{call test(?)}", SQL_NTS);

// Populate record 1 of ipd.
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,
                  30, 0, szQuote, 0, &amp;cbValue);

// Get ipd handle and set the SQL_DESC_NAMED and SQL_DESC_UNNAMED fields
// for record #1.
SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &amp;hIpd, 0, 0);
SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);

// Assuming that szQuote has been appropriately initialized,
// execute.
SQLExecute(hstmt);</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>