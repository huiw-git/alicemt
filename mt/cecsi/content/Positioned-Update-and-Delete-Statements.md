---
title: Positioned Update and Delete Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0eafba50-02c7-46ca-a439-ef3307b935dc
translation.priority.ht: 
  - en-gb
---
# Positioned Update and Delete Statements
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications can update or delete the current row in a result set with a positioned update or delete statement. Positioned update and delete statements are supported by some data sources, but not all of them. To determine whether a data source supports positioned update and delete statements, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1, or SQL_STATIC_CURSOR_ATTRIBUTES1 <legacyItalic>InfoType </legacyItalic>(depending on the type of the cursor). Note that the ODBC cursor library simulates positioned update and delete statements.</para>
    <para>To use a positioned update or delete statement, the application must create a result set with a <legacyBold>SELECT FOR UPDATE</legacyBold> statement. The syntax of this statement is:</para>
    <para>
      <legacyBold>SELECT </legacyBold>[<legacyBold>ALL</legacyBold> |<legacyBold> DISTINCT</legacyBold>] <legacyItalic>select-list</legacyItalic></para>
    <para>     <legacyBold>FROM</legacyBold> <legacyItalic>table-reference-list</legacyItalic> </para>
    <para>     [<legacyBold>WHERE</legacyBold> <legacyItalic>search-condition</legacyItalic>]</para>
    <para>     <legacyBold>FOR UPDATE OF </legacyBold>[<legacyItalic>column-name</legacyItalic> [<legacyBold>, </legacyBold><legacyItalic>column-name</legacyItalic>]...]</para>
    <para>The application then positions the cursor on the row to be updated or deleted. It can do this by calling <legacyBold>SQLFetchScroll</legacyBold> to retrieve a rowset containing the required row and calling <legacyBold>SQLSetPos</legacyBold> to position the rowset cursor on that row. The application then executes the positioned update or delete statement on a different statement than the statement being used by the result set. The syntax of these statements is:</para>
    <para>
      <legacyBold>UPDATE</legacyBold> <legacyItalic>table-name</legacyItalic> </para>
    <para>     <legacyBold>SET</legacyBold> <legacyItalic>column-identifier</legacyItalic><legacyBold> = </legacyBold>{<legacyItalic>expression</legacyItalic> | <legacyBold>NULL</legacyBold>}</para>
    <para>          [<legacyBold>,</legacyBold> <legacyItalic>column-identifier</legacyItalic><legacyBold> = </legacyBold>{<legacyItalic>expression</legacyItalic> | <legacyBold>NULL</legacyBold>}]...</para>
    <para>     <legacyBold>WHERE CURRENT OF </legacyBold><legacyItalic>cursor-name</legacyItalic></para>
    <para>
      <legacyBold>DELETE FROM</legacyBold> <legacyItalic>table-name</legacyItalic><legacyBold> WHERE CURRENT OF </legacyBold><legacyItalic>cursor-name</legacyItalic></para>
    <para>Notice that these statements require a cursor name. The application either can specify a cursor name with <legacyBold>SQLSetCursorName</legacyBold> before executing the statement that creates the result set or can let the data source automatically generate a cursor name when the cursor is created. In the latter case, the application retrieves this cursor name for use in positioned update and delete statements by calling <legacyBold>SQLGetCursorName</legacyBold>.</para>
    <para>For example, the following code allows a user to scroll through the Customers table and delete customer records or update their addresses and phone numbers. It calls <legacyBold>SQLSetCursorName</legacyBold> to specify a cursor name before it creates the result set of customers and uses three statement handles: <legacyItalic>hstmtCust</legacyItalic> for the result set, <legacyItalic>hstmtUpdate</legacyItalic> for a positioned update statement, and <legacyItalic>hstmtDelete</legacyItalic> for a positioned delete statement. Although the code could bind separate variables to the parameters in the positioned update statement, it updates the rowset buffers and binds the elements of these buffers. This keeps the rowset buffers synchronized with the updated data.</para>
    <code>#define POSITIONED_UPDATE 100
#define POSITIONED_DELETE 101

SQLUINTEGER    CustIDArray[10];
SQLCHAR        NameArray[10][51], AddressArray[10][51], 
               PhoneArray[10][11];
SQLINTEGER     CustIDIndArray[10], NameLenOrIndArray[10], 
               AddressLenOrIndArray[10],
               PhoneLenOrIndArray[10];
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;
SQLHSTMT       hstmtCust, hstmtUpdate, hstmtDelete;

// Set the SQL_ATTR_BIND_TYPE statement attribute to use column-wise 
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE 
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement 
// attribute to point to the row status array.
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);

// Bind arrays to the CustID, Name, Address, and Phone columns.
SQLBindCol(hstmtCust, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);
SQLBindCol(hstmtCust, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]),
            NameLenOrIndArray);
SQLBindCol(hstmtCust, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),
         AddressLenOrIndArray);
SQLBindCol(hstmtCust, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),
            PhoneLenOrIndArray);

// Set the cursor name to Cust.
SQLSetCursorName(hstmtCust, "Cust", SQL_NTS);

// Prepare positioned update and delete statements.
SQLPrepare(hstmtUpdate,
   "UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust",
   SQL_NTS);
SQLPrepare(hstmtDelete, "DELETE FROM Customers WHERE CURRENT OF Cust", SQL_NTS);

// Execute a statement to retrieve rows from the Customers table.
SQLExecDirect(hstmtCust,
   "SELECT CustID, Name, Address, Phone FROM Customers FOR UPDATE OF Address, Phone",
   SQL_NTS);

// Fetch and display the first 10 rows.
SQLFetchScroll(hstmtCust, SQL_FETCH_NEXT, 0);
DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray, AddressArray,
            AddressLenOrIndArray, PhoneArray, PhoneLenOrIndArray, RowStatusArray);

// Call GetAction to get an action and a row number from the user.
while (GetAction(&amp;Action, &amp;RowNum)) {
   switch (Action) {

      case SQL_FETCH_NEXT:
      case SQL_FETCH_PRIOR:
      case SQL_FETCH_FIRST:
      case SQL_FETCH_LAST:
      case SQL_FETCH_ABSOLUTE:
      case SQL_FETCH_RELATIVE:
         // Fetch and display the requested data.
         SQLFetchScroll(hstmtCust, Action, RowNum);
         DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray,
                     AddressArray, AddressLenOrIndArray, PhoneArray,
                     PhoneLenOrIndArray, RowStatusArray);
         break;

      case POSITIONED_UPDATE:
         // Get the new data and place it in the rowset buffers.
         GetNewData(AddressArray[RowNum - 1], &amp;AddressLenOrIndArray[RowNum - 1],
                     PhoneArray[RowNum - 1], &amp;PhoneLenOrIndArray[RowNum - 1]);

         // Bind the elements of the arrays at position RowNum-1 to the 
         // parameters of the positioned update statement.
         SQLBindParameter(hstmtUpdate, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,
                           50, 0, AddressArray[RowNum - 1], sizeof(AddressArray[0]),
                           &amp;AddressLenOrIndArray[RowNum - 1]);
         SQLBindParameter(hstmtUpdate, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,
                           10, 0, PhoneArray[RowNum - 1], sizeof(PhoneArray[0]),
                           &amp;PhoneLenOrIndArray[RowNum - 1]);

         // Position the rowset cursor. The rowset is 1-based.
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);

         // Execute the positioned update statement to update the row.
         SQLExecute(hstmtUpdate);
         break;

      case POSITIONED_DELETE:
         // Position the rowset cursor. The rowset is 1-based.
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);

         // Execute the positioned delete statement to delete the row.
         SQLExecute(hstmtDelete);
         break;
   }
}

// Close the cursor.
SQLCloseCursor(hstmtCust);</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>