---
title: Statement Parameters
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58d5b166-2578-4699-a560-1f1e6d86c49a
translation.priority.ht: 
  - en-gb
---
# Statement Parameters
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>parameter</legacyItalic> is a variable in an SQL statement. For example, suppose a Parts table has columns named PartID, Description, and Price. To add a part without parameters would require constructing an SQL statement such as:</para>
    <code>INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)</code>
    <para>Although this statement inserts a new order, it is not a good solution for an order entry application because the values to insert cannot be hard-coded in the application. An alternative is to construct the SQL statement at run time, using the values to be inserted. This is also not a good solution, because of the complexity of constructing statements at run time. The best solution is to replace the elements of the <legacyBold>VALUES</legacyBold> clause with question marks (?), or <legacyItalic>parameter markers</legacyItalic>:</para>
    <code>INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)</code>
    <para>The parameter markers are then bound to application variables. To add a new row, the application has only to set the values of the variables and execute the statement. The driver then retrieves the current values of the variables and sends them to the data source. If the statement will be executed multiple times, the application can make the process even more efficient by preparing the statement.</para>
    <para>The statement just shown might be hard-coded in an order entry application to insert a new row. However, parameter markers are not limited to vertical applications. For any application, they ease the difficulty of constructing SQL statements at run time by avoiding conversions to and from text. For example, the part ID just shown is most likely stored in the application as an integer. If the SQL statement is constructed without parameter markers, the application must convert the part ID to text and the data source must convert it back to an integer. By using a parameter marker, the application can send the part ID to the driver as an integer, which usually can send it to the data source as an integer. This saves two conversions. For long data values, this is very important, because the text forms of such values frequently exceed the allowed length of an SQL statement.</para>
    <para>Parameters are valid only in certain places in SQL statements. For example, they are not allowed in the select list (the list of columns to be returned by a <legacyBold>SELECT</legacyBold> statement), nor are they allowed as both operands of a binary operator such as the equal sign (=), because it would be impossible to determine the parameter type. Generally, parameters are valid only in Data Manipulation Language (DML) statements, and not in Data Definition Language (DDL) statements. For more information, see <legacyLink xlink:href="07213d04-cd31-45fd-a8c8-2e16e09eeaf4">Parameter Markers</legacyLink> in Appendix C: SQL Grammar.</para>
    <para>When the SQL statement invokes a procedure, named parameters can be used. Named parameters are identified by their names, not by their position in the SQL statement. They can be bound by a call to <legacyBold>SQLBindParameter</legacyBold>, but the parameter is identified by the SQL_DESC_NAME field of the IPD (implementation parameter descriptor), not by the <legacyItalic>ParameterNumber</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold>. They can also be bound by calling <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>. For more information about named parameters, see <legacyLink xlink:href="e2c3da5a-6c10-4dd5-acf9-e951eea71a6b">Binding Parameters by Name (Named Parameters)</legacyLink>, later in this section. For more information about descriptors, see <legacyLink xlink:href="ef2cbb93-cd00-40f8-b1d2-5f5723a991aa">Descriptors</legacyLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="7538a82b-b08b-4c8f-9809-e4ccea16db11">Binding Parameters</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="13e5da79-b60c-48d0-b467-773f481ef2a4">Setting Parameter Values</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ea989084-a8e6-4737-892e-9ec99dd49caf">Sending Long Data</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="54fd857e-d2cb-467d-bb72-121e67a8e88d">Procedure Parameters</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9b572c5b-1dfe-40af-bebd-051548ab6d90">Arrays of Parameter Values</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>