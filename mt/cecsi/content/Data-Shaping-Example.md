---
title: "Data Shaping Example"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1bfdcad4-52e1-45bc-ad21-783657ef0a44
caps.latest.revision: 12
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
# Data Shaping Example
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following data shaping command demonstrates how to build a hierarchical <legacyBold>Recordset</legacyBold> from the <legacyBold>Customers</legacyBold> and <legacyBold>Orders</legacyBold> tables in the Northwind database.</para>
    <code>SHAPE {SELECT CustomerID, ContactName FROM Customers} 
APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} AS chapOrders 
RELATE customerID TO customerID) </code>
    <para>When this command is used to open a <legacyBold>Recordset</legacyBold> object (as shown in <legacyLink xlink:href="d95dd499-19e2-4ce7-b16e-f56a04a9519c">Visual Basic Example of Data Shaping</legacyLink>), it creates a chapter (<legacyBold>chapOrders</legacyBold>) for each record returned from the <legacyBold>Customers</legacyBold> table. This chapter consists of a subset of the <legacyBold>Recordset</legacyBold> returned from the <legacyBold>Orders</legacyBold> table. The <legacyBold>chapOrders</legacyBold> chapter contains all the requested information about the orders placed by the given customer. In this example, the chapter consists of three columns: <legacyBold>OrderID</legacyBold>, <legacyBold>OrderDate</legacyBold>, and <legacyBold>CustomerID</legacyBold>. </para>
    <para>The first two entries of the resultant shaped <legacyBold>Recordset</legacyBold> are as follows:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>CustomerID</para>
          </TD>
          <TD>
            <para>ContactName</para>
          </TD>
          <TD>
            <para>OrderID</para>
          </TD>
          <TD>
            <para>OrderDate</para>
          </TD>
          <TD>
            <para>CustomerID</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>ALFKI</para>
          </TD>
          <TD>
            <para>Maria Ander</para>
          </TD>
          <TD>
            <para>10643</para>
            <para>10692</para>
            <para>10702</para>
            <para>10835</para>
            <para>10952</para>
            <para>11011</para>
          </TD>
          <TD>
            <para>1997-08-25</para>
            <para>1997-10-03</para>
            <para>1997-10-13</para>
            <para>1998-01-15</para>
            <para>1998-03-16</para>
            <para>1998-04-09</para>
          </TD>
          <TD>
            <para>ALFKI</para>
            <para>ALFKI</para>
            <para>ALFKI</para>
            <para>ALFKI</para>
            <para>ALFKI</para>
            <para>ALFKI</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ANATR</para>
          </TD>
          <TD>
            <para>Ana Trujillo</para>
          </TD>
          <TD>
            <para>10308</para>
            <para>10625</para>
            <para>10759</para>
            <para>10926</para>
          </TD>
          <TD>
            <para>1996-09-18</para>
            <para>1997-08-08</para>
            <para>1997-11-28</para>
            <para>1998-03-04</para>
          </TD>
          <TD>
            <para>ANATR</para>
            <para>ANATR</para>
            <para>ANATR</para>
            <para>ANATR</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>In a SHAPE command, APPEND is used to create a child <legacyBold>Recordset</legacyBold> related to the parent <legacyBold>Recordset</legacyBold> (as returned from the provider-specific command immediately after the SHAPE keyword that was discussed earlier) by the RELATE clause. The parent and child typically have at least one column in common: The value of the column in a row of the parent is the same as the value of the column in all rows of the child.</para>
    <para>There is a second way to use SHAPE commands: namely, to generate a parent <legacyBold>Recordset</legacyBold> from a child <legacyBold>Recordset</legacyBold>. The records in the child <legacyBold>Recordset</legacyBold> are grouped, typically by using the BY clause, and one row is added to the parent <legacyBold>Recordset</legacyBold> for each resulting group in the child. If the BY clause is omitted, the child <legacyBold>Recordset</legacyBold> will form a single group and the parent <legacyBold>Recordset</legacyBold> will contain exactly one row. This is useful for computing "grand total" aggregates over the entire child <legacyBold>Recordset</legacyBold>.</para>
    <para>The SHAPE command construct also enables you to programmatically create a shaped <legacyBold>Recordset</legacyBold>. You can then access the components of the <legacyBold>Recordset</legacyBold> programmatically or through an appropriate visual control. A shape command is issued like any other ADO command text. For more information, see <legacyLink xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</legacyLink>. </para>
    <para>Regardless of which way the parent <legacyBold>Recordset</legacyBold> is formed, it will contain a chapter column that is used to relate it to a child <legacyBold>Recordset</legacyBold>. If you want, the parent <legacyBold>Recordset</legacyBold> can also have columns that contain aggregates (SUM, MIN, MAX, and so on) over the child rows. Both the parent and the child <legacyBold>Recordset</legacyBold> can have columns that contain an expression on the row in the <legacyBold>Recordset</legacyBold>, as well as columns which are new and initially empty.</para>
    <para>This section continues with the following topic.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="d95dd499-19e2-4ce7-b16e-f56a04a9519c">Visual Basic Example of Data Shaping</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>