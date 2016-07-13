---
title: Updating Rows in the Rowset with SQLSetPos
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Updating Rows in the Rowset with SQLSetPos
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The update operation of <legacyBold>SQLSetPos</legacyBold> makes the data source update one or more selected rows of a table, using data in the application buffers for each bound column (unless the value in the length/indicator buffer is SQL_COLUMN_IGNORE). Columns that are not bound will not be updated.</para>
    <para>To update rows with <legacyBold>SQLSetPos</legacyBold>, the application does the following:  </para>
    <list class="ordered">
      <listItem>
        <para>Places the new data values in the rowset buffers. For information on how to send long data with <legacyBold>SQLSetPos</legacyBold>, see <legacyLink xlink:href="e2fdf842-5e4c-46ca-bb21-4625c3324f28">Long Data and SQLSetPos and SQLBulkOperations</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Sets the value in the length/indicator buffer of each column as necessary. This is the byte length of the data or SQL_NTS for columns bound to string buffers, the byte length of the data for columns bound to binary buffers, and SQL_NULL_DATA for any columns to be set to NULL.</para>
      </listItem>
      <listItem>
        <para>Sets the value in the length/indicator buffer of those columns which are not to be updated to SQL_COLUMN_IGNORE. Although the application can skip this step and resend existing data, this is inefficient and risks sending values to the data source that were truncated when they were read.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLSetPos</legacyBold> with <legacyItalic>Operation</legacyItalic> set to SQL_UPDATE and <legacyItalic>RowNumber</legacyItalic> set to the number of the row to update. If <legacyItalic>RowNumber</legacyItalic> is 0, all rows in the rowset are updated. </para>
      </listItem>
    </list>
    <para>After <legacyBold>SQLSetPos</legacyBold> returns, the current row is set to the updated row.</para>
    <para>When updating all rows of the rowset (<legacyItalic>RowNumber</legacyItalic> is equal to 0), an application can disable the update of certain rows by setting the corresponding elements of the row operation array (pointed to by the SQL_ATTR_ROW_OPERATION_PTR statement attribute) to SQL_ROW_IGNORE. The row operation array corresponds in size and number of elements to the row status array (pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute). To update only those rows in the result set that were successfully fetched and have not been deleted from the rowset, the application uses the row status array from the function that fetched the rowset as the row operation array to <legacyBold>SQLSetPos</legacyBold>.</para>
    <para>For every row that is sent to the data source as an update, the application buffers should have valid row data. If the application buffers were filled by fetching and if a row status array has been maintained, its values at each of these row positions should not be SQL_ROW_DELETED, SQL_ROW_ERROR, or SQL_ROW_NOROW.</para>
    <para>For example, the following code allows a user to scroll through the Customers table and update, delete, or add new rows. It places the new data in the rowset buffers before calling <legacyBold>SQLSetPos</legacyBold> to update or add new rows. An extra row is allocated at the end of the rowset buffers to hold new rows; this prevents existing data from being overwritten when data for a new row is placed in the buffers.</para>
    <code>#define UPDATE_ROW   100
#define DELETE_ROW   101
#define ADD_ROW      102

SQLUINTEGER    CustIDArray[11];
SQLCHAR        NameArray[11][51], AddressArray[11][51], 
               PhoneArray[11][11];
SQLINTEGER     CustIDIndArray[11], NameLenOrIndArray[11], 
               AddressLenOrIndArray[11],
               PhoneLenOrIndArray[11];
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;
SQLRETURN      rc;
SQLHSTMT       hstmt;

// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use column-wise 
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE 
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement 
// attribute to point to the row status array.
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_KEYSET_DRIVEN, 0);
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);

// Bind arrays to the CustID, Name, Address, and Phone columns.
SQLBindCol(hstmt, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);
SQLBindCol(hstmt, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]), NameLenOrIndArray);
SQLBindCol(hstmt, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),
            AddressLenOrIndArray);
SQLBindCol(hstmt, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),
            PhoneLenOrIndArray);

// Execute a statement to retrieve rows from the Customers table.
SQLExecDirect(hstmt, "SELECT CustID, Name, Address, Phone FROM Customers", SQL_NTS);

// Fetch and display the first 10 rows.
rc = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);
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
         SQLFetchScroll(hstmt, Action, RowNum);
         DisplayData(CustIDArray, CustIDIndArray,
                     NameArray, NameLenOrIndArray,
                     AddressArray, AddressLenOrIndArray,
                     PhoneArray, PhoneLenOrIndArray, RowStatusArray);
         break;

      case UPDATE_ROW:
         // Place the new data in the rowset buffers and update the 
         // specified row.
         GetNewData(&amp;CustIDArray[RowNum - 1], &amp;CustIDIndArray[RowNum - 1],
                  NameArray[RowNum - 1], &amp;NameLenOrIndArray[RowNum - 1],
                  AddressArray[RowNum - 1], &amp;AddressLenOrIndArray[RowNum - 1],
                  PhoneArray[RowNum - 1], &amp;PhoneLenOrIndArray[RowNum - 1]);
         SQLSetPos(hstmt, RowNum, SQL_UPDATE, SQL_LOCK_NO_CHANGE);
         break;

      case DELETE_ROW:
         // Delete the specified row.
         SQLSetPos(hstmt, RowNum, SQL_DELETE, SQL_LOCK_NO_CHANGE);
         break;

      case ADD_ROW:
         // Place the new data in the rowset buffers at index 10. 
         // This is an extra element for new rows so rowset data is 
         // not overwritten. Insert the new row. Row 11 corresponds 
         // to index 10.
         GetNewData(&amp;CustIDArray[10], &amp;CustIDIndArray[10],
                     NameArray[10], &amp;NameLenOrIndArray[10],
                     AddressArray[10], &amp;AddressLenOrIndArray[10],
                     PhoneArray[10], &amp;PhoneLenOrIndArray[10]);
         SQLSetPos(hstmt, 11, SQL_ADD, SQL_LOCK_NO_CHANGE);
         break;
   }
}

// Close the cursor.
SQLCloseCursor(hstmt);</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>