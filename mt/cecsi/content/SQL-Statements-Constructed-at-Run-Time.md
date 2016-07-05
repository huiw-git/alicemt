---
title: SQL Statements Constructed at Run Time
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
translation.priority.ht: 
  - en-gb
---
# SQL Statements Constructed at Run Time
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications that perform ad hoc analysis commonly build SQL statements at run time. For example, a spreadsheet might allow a user to select columns from which to retrieve data:</para>
    <code>// SQL_Statements_Constructed_at_Run_Time.cpp
#include &lt;windows.h&gt;
#include &lt;stdio.h&gt;
#include &lt;sqltypes.h&gt;

int main() {
   SQLCHAR *Statement = 0, *TableName = 0;
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;
   BOOL *ColumnSelectedArray = 0;
   BOOL  CommaNeeded;
   SQLSMALLINT i = 0, NumColumns = 0;

   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the
   // user select a table and store the selected table in TableName.

   // Use SQLColumns to build a list of the columns in the selected table
   // (ColumnNamesArray). Set NumColumns to the number of columns in the
   // table. Let the user select one or more columns and flag these columns
   // in ColumnSelectedArray[].

   // Build a SELECT statement from the selected columns.
   CommaNeeded = FALSE;
   Statement = (SQLCHAR*)malloc(8);
   strcpy_s((char*)Statement, 8, "SELECT ");

   for (i = 0 ; i = NumColumns ; i++) {
      if (ColumnSelectedArray[i]) {
         if (CommaNeeded)
            strcat_s((char*)Statement, sizeof(Statement), ",");
         else
            CommaNeeded = TRUE;
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);
      }
   }

   strcat_s((char*)Statement, 15, " FROM ");
   // strcat_s((char*)Statement, 100, (char*)TableName);

   // Execute the statement . It will be executed once, do not prepare it.
   // SQLExecDirect(hstmt, Statement, SQL_NTS);
}</code>
    <para>Another class of applications that commonly constructs SQL statements at run time are application development environments. However, the statements they construct are hard-coded in the application they are building, where they can usually be optimized and tested.</para>
    <para>Applications that construct SQL statements at run time can provide tremendous flexibility to the user. As can be seen from the preceding example, which did not even support such common operations as <legacyBold>WHERE</legacyBold> clauses, <legacyBold>ORDER BY</legacyBold> clauses, or joins, constructing SQL statements at run time is vastly more complex than hard-coding statements. Furthermore, testing such applications is problematic because they can construct an arbitrary number of SQL statements.</para>
    <para>A potential disadvantage of constructing SQL statements at run time is that it takes far more time to construct a statement than use a hard-coded statement. Fortunately, this is rarely a concern. Such applications tend to be user-interface intensive, and the time the application spends constructing SQL statements is generally small compared to the time the user spends entering criteria.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>