---
title: Binding Parameter Markers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Binding Parameter Markers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The application binds parameters by calling <legacyBold>SQLBindParameter</legacyBold>. <legacyBold>SQLBindParameter</legacyBold> binds one parameter at a time. With it, the application specifies the following:  </para>
    <list class="bullet">
      <listItem>
        <para>The parameter number. Parameters are numbered in increasing parameter order in the SQL statement, starting with the number 1. While it is legal to specify a parameter number that is higher than the number of parameters in the SQL statement, the parameter value will be ignored when the statement is executed.</para>
      </listItem>
      <listItem>
        <para>The parameter type (input, input/output, or output). Except for parameters in procedure calls, all parameters are input parameters. For more information, see <legacyLink xlink:href="54fd857e-d2cb-467d-bb72-121e67a8e88d">Procedure Parameters</legacyLink>, later in this section.</para>
      </listItem>
      <listItem>
        <para>The C data type, address, and byte length of the variable bound to the parameter. The driver must be able to convert the data from the C data type to the SQL data type or an error is returned. For a list of supported conversions, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink> in Appendix D: Data Types.</para>
      </listItem>
      <listItem>
        <para>The SQL data type, precision, and scale of the parameter itself.</para>
      </listItem>
      <listItem>
        <para>The address of a length/indicator buffer. It provides the byte length of binary or character data, specifies that the data is NULL, or specifies that the data will be sent with <legacyBold>SQLPutData</legacyBold>. For more information, see <legacyLink xlink:href="849792f1-cb1e-4bc2-b568-c0aff0b66199">Using Length/Indicator Values</legacyLink>.</para>
      </listItem>
    </list>
    <para>For example, the following code binds <legacyItalic>SalesPerson</legacyItalic> and <legacyItalic>CustID</legacyItalic> to parameters for the SalesPerson and CustID columns. Because <legacyItalic>SalesPerson</legacyItalic> contains character data, which is variable length, the code specifies the byte length of <legacyItalic>SalesPerson</legacyItalic> (11) and binds <legacyItalic>SalesPersonLenOrInd</legacyItalic> to contain the byte length of the data in <legacyItalic>SalesPerson</legacyItalic>. This information is not necessary for <legacyItalic>CustID</legacyItalic> because it contains integer data, which is of fixed length.</para>
    <code>SQLCHAR       SalesPerson[11];
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;
SQLUINTEGER   CustID;

// Bind SalesPerson to the parameter for the SalesPerson column and
// CustID to the parameter for the CustID column.
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,
                  SalesPerson, sizeof(SalesPerson), &amp;SalesPersonLenOrInd);
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,
                  &amp;CustID, 0, &amp;CustIDInd);

// Set values of salesperson and customer ID and length/indicators.
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");
SalesPersonLenOrInd = SQL_NTS;
CustID = 1331;
CustIDInd = 0;

// Execute a statement to get data for all orders made to the specified
// customer by the specified salesperson.
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);</code>
    <para>When <legacyBold>SQLBindParameter</legacyBold> is called, the driver stores this information in the structure for the statement. When the statement is executed, it uses the information to retrieve the parameter data and send it to the data source.</para>
    <alert class="note">
      <para>In ODBC 1.0, parameters were bound with <legacyBold>SQLSetParam</legacyBold>. The Driver Manager maps calls between <legacyBold>SQLSetParam</legacyBold> and <legacyBold>SQLBindParameter</legacyBold>, depending on the versions of ODBC used by the application and driver.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>