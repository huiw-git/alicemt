---
title: "Simulating Positioned Update and Delete Statements"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b24ed59f-f25b-4646-a135-5f3596abc1a4
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Simulating Positioned Update and Delete Statements
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If the data source does not support positioned update and delete statements, the driver can simulate these. For example, the ODBC cursor library simulates positioned update and delete statements. The general strategy for simulating positioned update and delete statements is to convert positioned statements to searched ones. This is done by replacing the <legacyBold>WHERE CURRENT OF</legacyBold> clause with a searched <legacyBold>WHERE</legacyBold> clause that identifies the current row.</para>
    <para>For example, because the CustID column uniquely identifies each row in the Customers table, the positioned delete statement</para>
    <code>DELETE FROM Customers WHERE CURRENT OF CustCursor</code>
    <para>might be converted to</para>
    <code>DELETE FROM Customers WHERE (CustID = ?)</code>
    <para>The driver may use one of the following <legacyItalic>row identifiers</legacyItalic> in the <legacyBold>WHERE</legacyBold> clause:  </para>
    <list class="bullet">
      <listItem>
        <para>Columns whose values serve to identify uniquely every row in the table. For example, calling <legacyBold>SQLSpecialColumns</legacyBold> with SQL_BEST_ROWID returns the optimal column or set of columns that serve this purpose.</para>
      </listItem>
      <listItem>
        <para>Pseudo-columns, provided by some data sources, for the purpose of uniquely identifying every row. These may also be retrievable by calling <legacyBold>SQLSpecialColumns</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>A unique index, if available.</para>
      </listItem>
      <listItem>
        <para>All the columns in the result set.</para>
      </listItem>
    </list>
    <para>Exactly which columns a driver should use in the <legacyBold>WHERE</legacyBold> clause it constructs depends on the driver. On some data sources, determining a row identifier can be costly. However, it is faster to execute and guarantees that a simulated statement updates or deletes at most one row. Depending on the capabilities of the underlying DBMS, using a row identifier can be expensive to set up. However, it is faster to execute and guarantees that a simulated statement will update or delete only one row. The option of using all the columns in the result set is usually much easier to set up. However, it is slower to execute and, if the columns do not uniquely identify a row, can result in rows being unintentionally updated or deleted, especially when the select list for the result set does not contain all the columns that exist in the underlying table.</para>
    <para>Depending upon which of the preceding strategies the driver supports, an application can choose which strategy it wants the driver to use with the SQL_ATTR_SIMULATE_CURSOR statement attribute. Although it might seem odd for an application to risk unintentionally updating or deleting a row, the application can remove this risk by ensuring that the columns in the result set uniquely identify each row in the result set. This saves the driver the effort of having to do this.</para>
    <para>If the driver chooses to use a row identifier, it intercepts the <legacyBold>SELECT FOR UPDATE</legacyBold> statement that creates the result set. If the columns in the select list do not effectively identify a row, the driver adds the necessary columns to the end of the select list. Some data sources have a single column that always uniquely identifies a row, such as the ROWID column in Oracle; if such a column is available, the driver uses this. Otherwise, the driver calls <legacyBold>SQLSpecialColumns</legacyBold> for each table in the <legacyBold>FROM</legacyBold> clause to retrieve a list of the columns that uniquely identify each row. A common restriction that results from this technique is that cursor simulation fails if there is more than one table in the <legacyBold>FROM</legacyBold> clause. </para>
    <para>No matter how the driver identifies rows, it usually strips the <legacyBold>FOR UPDATE OF</legacyBold> clause off the <legacyBold>SELECT FOR UPDATE</legacyBold> statement before sending it to the data source. The <legacyBold>FOR UPDATE OF</legacyBold> clause is used only with positioned update and delete statements. Data sources that do not support positioned update and delete statements generally do not support it.</para>
    <para>When the application submits a positioned update or delete statement for execution, the driver replaces the <legacyBold>WHERE CURRENT OF</legacyBold> clause with a <legacyBold>WHERE</legacyBold> clause containing the row identifier. The values of these columns are retrieved from a cache maintained by the driver for each column it uses in the <legacyBold>WHERE</legacyBold> clause. After the driver has replaced the <legacyBold>WHERE</legacyBold> clause, it sends the statement to the data source for execution.</para>
    <para>For example, suppose that the application submits the following statement to create a result set:</para>
    <code>SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address</code>
    <para>If the application has set SQL_ATTR_SIMULATE_CURSOR to request a guarantee of uniqueness and if the data source does not provide a pseudo-column that always uniquely identifies a row, the driver calls <legacyBold>SQLSpecialColumns</legacyBold> for the Customers table, discovers that CustID is the key to the Customers table and adds this to the select list, and strips the <legacyBold>FOR UPDATE OF</legacyBold> clause:</para>
    <code>SELECT Name, Address, Phone, CustID FROM Customers</code>
    <para>If the application has not requested a guarantee of uniqueness, the driver strips only the <legacyBold>FOR UPDATE OF</legacyBold> clause:</para>
    <code>SELECT Name, Address, Phone FROM Customers</code>
    <para>Suppose the application scrolls through the result set and submits the following positioned update statement for execution, where Cust is the name of the cursor over the result set:</para>
    <code>UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust</code>
    <para>If the application has not requested a guarantee of uniqueness, the driver replaces the <legacyBold>WHERE</legacyBold> clause and binds the CustID parameter to the variable in its cache:</para>
    <code>UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)</code>
    <para>If the application has not requested a guarantee of uniqueness, the driver replaces the <legacyBold>WHERE</legacyBold> clause and binds the Name, Address, and Phone parameters in this clause to the variables in its cache:</para>
    <code>UPDATE Customers SET Address = ?, Phone = ?
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>