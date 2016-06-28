---
title: Connecting with SQLConnect
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b16319d2-2c2c-4341-abb5-caa9e17362b4
translation.priority.ht: 
  - en-gb
---
# Connecting with SQLConnect
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>SQLConnect</legacyBold> is the simplest connection function. It requires a data source name and accepts an optional user ID and password. It works well for applications that hard-code a data source name and do not require a user ID or password. It also works well for applications that want to control their own "look and feel" or that have no user interface. Such applications can build a list of data sources using <legacyBold>SQLDataSources</legacyBold>, prompt the user for data source, user ID, and password, and then call <legacyBold>SQLConnect</legacyBold>.</para>
    <para>The following example connects to the Northwind database, using a DSN called Northwind, and retrieves all of the first and last name fields from all of the records in the Employees table.</para>
    <code>// Connecting_with_SQLConnect.cpp
// compile with: user32.lib odbc32.lib
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;
#include &lt;mbstring.h&gt;
#include &lt;stdio.h&gt;

#define MAX_DATA 100
#define MYSQLSUCCESS(rc) ((rc == SQL_SUCCESS) || (rc == SQL_SUCCESS_WITH_INFO) )

class direxec {
   RETCODE rc; // ODBC return code
   HENV henv; // Environment   
   HDBC hdbc; // Connection handle
   HSTMT hstmt; // Statement handle

   unsigned char szData[MAX_DATA]; // Returned data storage
   SDWORD cbData; // Output length of data
   unsigned char chr_ds_name[SQL_MAX_DSN_LENGTH]; // Data source name

public:
   direxec(); // Constructor
   void sqlconn(); // Allocate env, stat, and conn
   void sqlexec(unsigned char *); // Execute SQL statement
   void sqldisconn(); // Free pointers to env, stat, conn, and disconnect
   void error_out(); // Displays errors
};

// Constructor initializes the string chr_ds_name with the data source name.
// "Northwind" is an ODBC data source (odbcad32.exe) name whose default is the Northwind database
direxec::direxec() {
   _mbscpy_s(chr_ds_name, SQL_MAX_DSN_LENGTH, (const unsigned char *)"Northwind");
}

// Allocate environment handle and connection handle, connect to data source, and allocate statement handle.
void direxec::sqlconn() {
   SQLAllocEnv(&amp;henv);
   SQLAllocConnect(henv, &amp;hdbc);
   rc = SQLConnect(hdbc, chr_ds_name, SQL_NTS, NULL, 0, NULL, 0);

   // Deallocate handles, display error message, and exit.
   if (!MYSQLSUCCESS(rc)) {
      SQLFreeConnect(henv);
      SQLFreeEnv(henv);
      SQLFreeConnect(hdbc);
      if (hstmt)
         error_out();
      exit(-1);
   }

   rc = SQLAllocStmt(hdbc, &amp;hstmt);
}

// Execute SQL command with SQLExecDirect() ODBC API.
void direxec::sqlexec(unsigned char * cmdstr) {
   rc = SQLExecDirect(hstmt, cmdstr, SQL_NTS);
   if (!MYSQLSUCCESS(rc)) {  //Error
      error_out();
      // Deallocate handles and disconnect.
      SQLFreeStmt(hstmt,SQL_DROP);
      SQLDisconnect(hdbc);
      SQLFreeConnect(hdbc);
      SQLFreeEnv(henv);
      exit(-1);
   }
   else {
      for ( rc = SQLFetch(hstmt) ; rc == SQL_SUCCESS ; rc=SQLFetch(hstmt) ) {
         SQLGetData(hstmt, 1, SQL_C_CHAR, szData, sizeof(szData), &amp;cbData);
         // In this example, the data is sent to the console; SQLBindCol() could be called to bind 
         // individual rows of data and assign for a rowset.
         printf("%s\n", (const char *)szData);
      }
   }
}

// Free the statement handle, disconnect, free the connection handle, and free the environment handle.
void direxec::sqldisconn() {
   SQLFreeStmt(hstmt,SQL_DROP);
   SQLDisconnect(hdbc);
   SQLFreeConnect(hdbc);
   SQLFreeEnv(henv);
}

// Display error message in a message box that has an OK button.
void direxec::error_out() {
   unsigned char szSQLSTATE[10];
   SDWORD nErr;
   unsigned char msg[SQL_MAX_MESSAGE_LENGTH + 1];
   SWORD cbmsg;

   while (SQLError(0, 0, hstmt, szSQLSTATE, &amp;nErr, msg, sizeof(msg), &amp;cbmsg) == SQL_SUCCESS) {
      sprintf_s((char *)szData, sizeof(szData), "Error:\nSQLSTATE=%s, Native error=%ld, msg='%s'", szSQLSTATE, nErr, msg);
      MessageBox(NULL, (const char *)szData, "ODBC Error", MB_OK);
   }
}

int main () {
   direxec x;   // Declare an instance of the direxec object.
   x.sqlconn();   // Allocate handles, and connect.
   x.sqlexec((UCHAR FAR *)"SELECT FirstName, LastName FROM employees");   // Execute SQL command
   x.sqldisconn();   // Free handles and disconnect
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>