---
title: Cursors
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e668b40c-bd4d-4415-850d-20fc4872ee72
---
# Cursors
  Operations in a relational database act on a complete set of rows. For example, the set of rows returned by a SELECT statement consists of all the rows that satisfy the conditions in the WHERE clause of the statement. This complete set of rows returned by the statement is known as the result set. Applications, especially interactive online applications, cannot always work effectively with the entire result set as a unit. These applications need a mechanism to work with one row or a small block of rows at a time. Cursors are an extension to result sets that provide that mechanism.  
  
 Cursors extend result processing by:  
  
-   Allowing positioning at specific rows of the result set.  
  
-   Retrieving one row or block of rows from the current position in the result set.  
  
-   Supporting data modifications to the rows at the current position in the result set.  
  
-   Supporting different levels of visibility to changes made by other users to the database data that is presented in the result set.  
  
-   Providing [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements in scripts, stored procedures, and triggers access to the data in a result set.  
  
## Concepts  
 Cursor Implementations  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports three cursor implementations.  
  
 Transact\-SQL cursors  
 Are based on the DECLARE CURSOR syntax and are used mainly in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts, stored procedures, and triggers. [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] cursors are implemented on the server and are managed by [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements sent from the client to the server. They may also be contained in batches, stored procedures, or triggers.  
  
 Application programming interface \(API\) server cursors  
 Support the API cursor functions in OLE DB and ODBC. API server cursors are implemented on the server. Each time a client application calls an API cursor function, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client OLE DB provider or ODBC driver transmits the request to the server for action against the API server cursor.  
  
 Client cursors  
 Are implemented internally by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client ODBC driver and by the DLL that implements the ADO API. Client cursors are implemented by caching all the result set rows on the client. Each time a client application calls an API cursor function, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client ODBC driver or the ADO DLL performs the cursor operation on the result set rows cached on the client.  
  
 Type of Cursors  
 Forward\-only  
 A forward\-only cursor does not support scrolling; it supports only fetching the rows serially from the start to the end of the cursor. The rows are not retrieved from the database until they are fetched. The effects of all INSERT, UPDATE, and DELETE statements made by the current user or committed by other users that affect rows in the result set are visible as the rows are fetched from the cursor.  
  
 Because the cursor cannot be scrolled backward, most changes made to rows in the database after the row was fetched are not visible through the cursor. In cases where a value used to determine the location of the row within the result set is modified, such as updating a column covered by a clustered index, the modified value is visible through the cursor.  
  
 Although the database API cursor models consider a forward\-only cursor to be a distinct type of cursor, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] considers both forward\-only and scroll as options that can be applied to static, keyset\-driven, and dynamic cursors. [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] cursors support forward\-only static, keyset\-driven, and dynamic cursors. The database API cursor models assume that static, keyset\-driven, and dynamic cursors are always scrollable. When a database API cursor attribute or property is set to forward\-only, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] implements this as a forward\-only dynamic cursor.  
  
 Static  
 The complete result set of a static cursor is built in **tempdb** when the cursor is opened. A static cursor always displays the result set as it was when the cursor was opened. Static cursors detect few or no changes, but consume relatively few resources while scrolling.  
  
 The cursor does not reflect any changes made in the database that affect either the membership of the result set or changes to the values in the columns of the rows that make up the result set. A static cursor does not display new rows inserted in the database after the cursor was opened, even if they match the search conditions of the cursor SELECT statement. If rows making up the result set are updated by other users, the new data values are not displayed in the static cursor. The static cursor displays rows deleted from the database after the cursor was opened. No UPDATE, INSERT, or DELETE operations are reflected in a static cursor \(unless the cursor is closed and reopened\), not even modifications made using the same connection that opened the cursor.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] static cursors are always read\-only.  
  
 Because the result set of a static cursor is stored in a work table in **tempdb**, the size of the rows in the result set cannot exceed the maximum row size for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table.  
  
 [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] uses the term insensitive for static cursors. Some database APIs identify them as snapshot cursors.  
  
 Keyset  
 The membership and order of rows in a keyset\-driven cursor are fixed when the cursor is opened. Keyset\-driven cursors are controlled by a set of unique identifiers, keys, known as the keyset. The keys are built from a set of columns that uniquely identify the rows in the result set. The keyset is the set of the key values from all the rows that qualified for the SELECT statement at the time the cursor was opened. The keyset for a keyset\-driven cursor is built in **tempdb** when the cursor is opened.  
  
 Dynamic  
 Dynamic cursors are the opposite of static cursors. Dynamic cursors reflect all changes made to the rows in their result set when scrolling through the cursor. The data values, order, and membership of the rows in the result set can change on each fetch. All UPDATE, INSERT, and DELETE statements made by all users are visible through the cursor. Updates are visible immediately if they are made through the cursor using either an API function such as **SQLSetPos** or the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] WHERE CURRENT OF clause. Updates made outside the cursor are not visible until they are committed, unless the cursor transaction isolation level is set to read uncommitted. Dynamic cursor plans never use spatial indexes.  
  
## Requesting a Cursor  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports two methods for requesting a cursor:  
  
-   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]  
  
     The [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] language supports a syntax for using cursors modeled after the ISO cursor syntax.  
  
-   Database application programming interface \(API\) cursor functions  
  
     [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports the cursor functionality of these database APIs:  
  
    -   ADO \([!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] ActiveX Data Object\)  
  
    -   OLE DB  
  
    -   ODBC \(Open Database Connectivity\)  
  
 An application should never mix these two methods of requesting a cursor. An application that has used the API to specify cursor behaviors should not then execute a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] DECLARE CURSOR statement to also request a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] cursor. An application should only execute DECLARE CURSOR if it has set all the API cursor attributes back to their defaults.  
  
 If neither a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] nor API cursor has been requested, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] defaults to returning a complete result set, known as a default result set, to the application.  
  
## Cursor Process  
 [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] cursors and API cursors have different syntax, but the following general process is used with all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cursors:  
  
1.  Associate a cursor with the result set of a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement, and define characteristics of the cursor, such as whether the rows in the cursor can be updated.  
  
2.  Execute the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement to populate the cursor.  
  
3.  Retrieve the rows in the cursor you want to see. The operation to retrieve one row or one block of rows from a cursor is called a fetch. Performing a series of fetches to retrieve rows in either a forward or backward direction is called scrolling.  
  
4.  Optionally, perform modification operations \(update or delete\) on the row at the current position in the cursor.  
  
5.  Close the cursor.  
  
## Related Content  
 [Cursor Behaviors](../Topic/Cursor%20Behaviors.md) [How Cursors Are Implemented](../Topic/How%20Cursors%20Are%20Implemented.md)  
  
## See Also  
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../Topic/DECLARE%20CURSOR%20\(Transact-SQL\).md)   
 [Cursors &#40;Transact-SQL&#41;](../Topic/Cursors%20\(Transact-SQL\).md)   
 [Cursor Functions &#40;Transact-SQL&#41;](../Topic/Cursor%20Functions%20\(Transact-SQL\).md)   
 [Cursor Stored Procedures &#40;Transact-SQL&#41;](../Topic/Cursor%20Stored%20Procedures%20\(Transact-SQL\).md)  
  
  