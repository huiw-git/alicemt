---
title: Binding Parameters ODBC
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7538a82b-b08b-4c8f-9809-e4ccea16db11
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Binding Parameters ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each parameter in an SQL statement must be associated, or <legacyItalic>bound,</legacyItalic> to a variable in the application before the statement is executed. When the application binds a variable to a parameter, it describes that variable — address, C data type, and so on — to the driver. It also describes the parameter itself — SQL data type, precision, and so on. The driver stores this information in the structure it maintains for that statement and uses the information to retrieve the value from the variable when the statement is executed.</para>
    <para>Parameters can be bound or rebound at any time before a statement is executed. If a parameter is rebound after a statement is executed, the binding does not apply until the statement is executed again. To bind a parameter to a different variable, an application simply rebinds the parameter with the new variable; the previous binding is automatically released.</para>
    <para>A variable remains bound to a parameter until a different variable is bound to the parameter, until all parameters are unbound by calling <legacyBold>SQLFreeStmt</legacyBold> with the SQL_RESET_PARAMS option, or until the statement is released. For this reason, the application must be sure that variables are not freed until after they are unbound. For more information, see <legacyLink xlink:href="886bc9ed-39d4-43d2-82ff-aebc35b14d39">Allocating and Freeing Buffers</legacyLink>.</para>
    <para>Because parameter bindings are just information stored in the structure maintained by the driver for the statement, they can be set in any order. They are also independent of the SQL statement that is executed. For example, suppose an application binds three parameters and then executes the following SQL statement:</para>
    <code>INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)</code>
    <para>If the application then immediately executes the SQL statement</para>
    <code>SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?</code>
    <para>on the same statement handle, the parameter bindings for the <legacyBold>INSERT</legacyBold> statement are used because those are the bindings stored in the statement structure. In most cases, this is a poor programming practice and should be avoided. Instead, the application should call <legacyBold>SQLFreeStmt</legacyBold> with the SQL_RESET_PARAMS option to unbind all the old parameters and then bind new ones.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="fe88c1c2-4ee4-45e0-8500-b8c25c047815">Binding Parameter Markers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e2c3da5a-6c10-4dd5-acf9-e951eea71a6b">Binding Parameters by Name (Named Parameters)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c">Parameter Binding Offsets</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="118d0f47-2afd-4955-bb47-38b1e2c2f38f">Describing Parameters</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>