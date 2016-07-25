---
title: "Handles"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Handles
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Handles are opaque, 32-bit values that identify a particular item; in ODBC, this item can be an environment, connection, statement, or descriptor. When the application calls <legacyBold>SQLAllocHandle</legacyBold>, the Driver Manager or driver creates a new item of the specified type and returns its handle to the application. The application later uses the handle to identify that item when calling ODBC functions. The Driver Manager and driver use the handle to locate information about the item.</para>
    <para>For example, the following code uses two statement handles (<legacyItalic>hstmtOrder</legacyItalic> and <legacyItalic>hstmtLine</legacyItalic>) to identify the statements on which to create result sets of sales orders and sales order line numbers. It later uses these handles to identify which result set to fetch data from.</para>
    <code>SQLHSTMT      hstmtOrder, hstmtLine; // Statement handles.
SQLUINTEGER   OrderID;
SQLINTEGER    OrderIDInd = 0;
SQLRETURN     rc;

// Prepare the statement that retrieves line number information.
SQLPrepare(hstmtLine, "SELECT * FROM Lines WHERE OrderID = ?", SQL_NTS);

// Bind OrderID to the parameter in the preceding statement.
SQLBindParameter(hstmtLine, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,
               &amp;OrderID, 0, &amp;OrderIDInd);

// Bind the result sets for the Order table and the Lines table. Bind
// OrderID to the OrderID column in the Orders table. When each row is
// fetched, OrderID will contain the current order ID, which will then be
// passed as a parameter to the statement tofetch line number
// information. Code not shown.

// Create a result set of sales orders.
SQLExecDirect(hstmtOrder, "SELECT * FROM Orders", SQL_NTS);

// Fetch and display the sales order data. Code to check if rc equals
// SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.
while ((rc = SQLFetch(hstmtOrder)) != SQL_NO_DATA) {
   // Display the sales order data. Code not shown.

   // Create a result set of line numbers for the current sales order.
   SQLExecute(hstmtLine);

   // Fetch and display the sales order line number data. Code to check
   // if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.
   while ((rc = SQLFetch(hstmtLine)) != SQL_NO_DATA) {
      // Display the sales order line number data. Code not shown.
   }

   // Close the sales order line number result set.
   SQLCloseCursor(hstmtLine);
}

// Close the sales order result set.
SQLCloseCursor(hstmtOrder);</code>
    <para>Handles are meaningful only to the ODBC component that created them; that is, only the Driver Manager can interpret Driver Manager handles and only a driver can interpret its own handles.</para>
    <para>For example, suppose the driver in the preceding example allocates a structure to store information about a statement and returns the pointer to this structure as the statement handle. When the application calls <legacyBold>SQLPrepare</legacyBold>, it passes an SQL statement and the handle of the statement used for sales order line numbers. The driver sends the SQL statement to the data source, which prepares it and returns an access plan identifier. The driver uses the handle to find the structure in which to store this identifier.</para>
    <para>Later, when the application calls <legacyBold>SQLExecute</legacyBold> to generate the result set of line numbers for a particular sales order, it passes the same handle. The driver uses the handle to retrieve the access plan identifier from the structure. It sends the identifier to the data source to tell it which plan to execute.</para>
    <para>ODBC has two levels of handles: Driver Manager handles and driver handles. The application uses Driver Manager handles when calling ODBC functions because it calls those functions in the Driver Manager. The Driver Manager uses this handle to find the corresponding driver handle and uses the driver handle when calling the function in the driver. For an example of how driver and Driver Manager handles are used, see <legacyLink xlink:href="77c05630-5a8b-467d-b80e-c705dc06d601">Driver Manager's Role in the Connection Process</legacyLink>.</para>
    <para>That there are two levels of handles is an artifact of the ODBC architecture; in most cases, it is not relevant to either the application or driver. Although there is usually no reason to do so, it is possible for the application to determine the driver handles by calling <legacyBold>SQLGetInfo</legacyBold>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="917f1b0c-272b-4e37-a1f5-87cd24b9fa21">Environment Handles</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="12222653-f04d-46d6-bdee-61348f5d550f">Connection Handles</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="65d6d78b-a8c8-489a-9dad-f8d127a44882">Statement Handles</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="7741035c-f3e7-4c89-901e-fe528392f67d">Descriptor Handles</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="fc741611-6535-43cc-8156-6d897d04664e">State Transitions</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>