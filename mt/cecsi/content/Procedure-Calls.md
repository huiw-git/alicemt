---
title: "Procedure Calls"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 145130cc-40e7-4722-8417-dff131084752
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Procedure Calls
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>procedure</legacyItalic> is an executable object stored on the data source. Generally, it is one or more SQL statements that have been precompiled. The escape sequence for calling a procedure is</para>
    <para>         <legacyBold>{</legacyBold>[<legacyBold>?=</legacyBold>]<legacyBold>call</legacyBold> <legacyItalic>procedure-name</legacyItalic>[<legacyBold>(</legacyBold>[<legacyItalic>parameter</legacyItalic>][<legacyBold>,</legacyBold>[<legacyItalic>parameter</legacyItalic>]]...<legacyBold>)</legacyBold>]<legacyBold>}</legacyBold></para>
    <para>where <legacyItalic>procedure-name</legacyItalic> specifies the name of a procedure and <legacyItalic>parameter</legacyItalic> specifies a procedure parameter.</para>
    <para>For more information about the procedure call escape sequence, see <legacyLink xlink:href="269fbab0-e5f2-4a98-86c0-2d7b647acaae">Procedure Call Escape Sequence</legacyLink> in Appendix C: SQL Grammar.</para>
    <para>A procedure can have zero or more parameters. It can also return a value, as indicated by the optional parameter marker <legacyBold>?=</legacyBold> at the start of the syntax. If <legacyItalic>parameter</legacyItalic> is an input or an input/output parameter, it can be a literal or a parameter marker. However, interoperable applications should always use parameter markers because some data sources do not accept literal parameter values. If <legacyItalic>parameter</legacyItalic> is an output parameter, it must be a parameter marker. Parameter markers must be bound with <legacyBold>SQLBindParameter</legacyBold> before the procedure call statement is executed.</para>
    <para>Input and input/output parameters can be omitted from procedure calls. If a procedure is called with parentheses but without any parameters, such as {call <legacyItalic>procedure-name</legacyItalic>()}, the driver instructs the data source to use the default value for the first parameter. If the procedure does not have any parameters, this might cause the procedure to fail. If a procedure is called without parentheses, such as {call <legacyItalic>procedure-name</legacyItalic>}, the driver does not send any parameter values.</para>
    <para>Literals can be specified for input and input/output parameters in procedure calls. For example, suppose the procedure <legacyBold>InsertOrder</legacyBold> has five input parameters. The following call to <legacyBold>InsertOrder</legacyBold> omits the first parameter, provides a literal for the second parameter, and uses a parameter marker for the third, fourth, and fifth parameters:</para>
    <code>{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!</code>
    <para>Notice that if a parameter is omitted, the comma delimiting it from other parameters must still appear. If an input or input/output parameter is omitted, the procedure uses the default value of the parameter. Another way to specify the default value of an input or input/output parameter is to set the value of the length/indicator buffer bound to the parameter to SQL_DEFAULT_PARAM.</para>
    <para>If an input/output parameter is omitted or if a literal is supplied for the parameter, the driver discards the output value. Similarly, if the parameter marker for the return value of a procedure is omitted, the driver discards the return value. Finally, if an application specifies a return value parameter for a procedure that does not return a value, the driver sets the value of the length/indicator buffer bound to the parameter to SQL_NULL_DATA.</para>
    <para>Suppose the procedure PARTS_IN_ORDERS creates a result set that contains a list of orders that contain a particular part number. The following code calls this procedure for part number 544:</para>
    <code>SQLUINTEGER   PartID;
SQLINTEGER    PartIDInd = 0;

// Bind the parameter.
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_SLONG, SQL_INTEGER, 0, 0,
                  &amp;PartID, 0, PartIDInd);

// Place the department number in PartID.
PartID = 544;

// Execute the statement.
SQLExecDirect(hstmt, "{call PARTS_IN_ORDERS(?)}", SQL_NTS);</code>
    <para>To determine whether a data source supports procedures, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_PROCEDURES option.</para>
    <para>For more information about procedures, see <legacyLink xlink:href="92172f52-6bd2-4b17-9ef0-baf1a97f7510">Procedures</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>