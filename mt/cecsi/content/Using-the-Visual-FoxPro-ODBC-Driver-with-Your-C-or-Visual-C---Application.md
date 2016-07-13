---
title: Using the Visual FoxPro ODBC Driver with Your C or Visual C++ Application
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: beb11a68-849e-4fe0-b217-d3722b1b1389
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using the Visual FoxPro ODBC Driver with Your C or Visual C++ Application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Your C or C++ application communicates with Visual FoxPro data by sending a <legacyLink xlink:href="cce0c25f-fa85-4cf5-bfee-4b7a9401f585">SQLExecute</legacyLink> or <legacyLink xlink:href="5004060f-8510-4018-87a4-d41789e69d3e">SQLExecDirect</legacyLink> statement to Visual FoxPro. This statement can contain the following:  </para>
    <list class="bullet">
      <listItem>
        <para>SQL statements native to the Visual FoxPro language, such as the <legacyLink xlink:href="bc50459b-8861-4889-84a9-129ae9065aa8">DROP TABLE</legacyLink> command.</para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="f41a38c2-e22e-4c65-a32e-9a6777435160">Supported ODBC SQL grammar</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Non-SQL Visual FoxPro language such as <legacyLink xlink:href="43a821fb-97fd-4316-aafe-4ef2de783188">supported SET commands</legacyLink>.</para>
      </listItem>
    </list>
    <para>For more information about SQL native to Visual FoxPro, see the Visual FoxPro documentation.</para>
  </introduction>
  <section>
    <title>Example: Using the Visual FoxPro ODBC Driver with Your C or C++ Application</title>
    <content>
      <para>The following example uses the ODBC C API to retrieve data stored in the last_name field in the employee table in the Microsoft® Visual FoxPro sample database named TasTrade. This database is provided with Visual FoxPro and is installed by default in the following location:</para>
      <para>
        <codeInline>c:\vfp\samples\mainsamp\data\tastrade.dbc</codeInline>
      </para>
      <para>The example displays one last name at a time, allowing you to click OK on the message box to see the next last name. It is assumed that a data source named Tastrade has been set up to use the Tastrade.dbc database.</para>
      <alert class="note">
        <para>Error checking should be performed on all ODBC API calls; this example excludes error checking for the sake of brevity.</para>
      </alert>
      <code>// FoxPro_ODBC_Driver_with_C.cpp
// compile with: odbc32.lib user32.lib /c
#include &lt;windows.h&gt;
#include &lt;sql.h&gt;
#include &lt;sqlext.h&gt;
#include &lt;stdio.h&gt;
#include &lt;mbstring.h&gt;

#define MAX_DATA 100
#define MYSQLSUCCESS(rc) ((rc==SQL_SUCCESS)||(rc==SQL_SUCCESS_WITH_INFO))

class direxec {
   RETCODE rc;        // ODBC return code
   HENV henv;         // Environment   
   HDBC hdbc;         // Connection handle
   HSTMT hstmt;       // Statement handle
   unsigned char szData[MAX_DATA];   // Returned data storage
   SDWORD cbData;     // Output length of data
   unsigned char chr_ds_name[SQL_MAX_DSN_LENGTH];   // Data source name

public:
   direxec();           // Constructor
   void sqlconn();      // Allocate env, stat, and conn
   void sqlexec(unsigned char *);   // Execute SQL statement
   void sqldisconn();   // Free pointers to env, stat, conn, and disconnect
   void error_out();    // Displays errors
};

// Constructor initializes the string chr_ds_name with the data source name.
direxec::direxec() {
   _mbscpy_s(chr_ds_name, (const unsigned char *)"tastrade");
}

// Allocate environment handle, allocate connection handle,
// connect to data source, and allocate statement handle.
void direxec::sqlconn() {
   SQLAllocEnv(&amp;henv);
   SQLAllocConnect(henv, &amp;hdbc);
   rc=SQLConnect(hdbc, chr_ds_name, SQL_NTS, NULL, 0, NULL, 0);

   // Deallocate handles, display error message, and exit.
   if (!MYSQLSUCCESS(rc)) {
      SQLFreeEnv(henv);
      SQLFreeConnect(hdbc);
      error_out();
      exit(-1);
   }

   rc = SQLAllocStmt(hdbc, &amp;hstmt);
}

// Execute SQL command with SQLExecDirect() ODBC API.
void direxec::sqlexec(unsigned char * cmdstr) {
   rc = SQLExecDirect(hstmt, cmdstr, SQL_NTS);
   if (!MYSQLSUCCESS(rc)) {   // Error
      error_out();
      // Deallocate handles and disconnect.
      SQLFreeStmt(hstmt, SQL_DROP);
      SQLDisconnect(hdbc);
      SQLFreeConnect(hdbc);
      SQLFreeEnv(henv);
      exit(-1);
   }
   else {
      for (rc = SQLFetch(hstmt) ; rc == SQL_SUCCESS; rc=SQLFetch(hstmt)) {
         SQLGetData(hstmt, 1, SQL_C_CHAR, szData, sizeof(szData), &amp;cbData);
         // In this example, the data is returned in a messagebox for
         // simplicity. However, normally the SQLBindCol() ODBC API could
         // be called to bind individual data rows and assign for a rowset.
         MessageBox(NULL, (const char *)szData, "ODBC", MB_OK);
      }
   }
}

// Free the statement handle, disconnect, free the connection handle, and
// free the environment handle.
void direxec::sqldisconn() {
   SQLFreeStmt(hstmt, SQL_DROP);
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

   while(SQLError(0, 0, hstmt, szSQLSTATE, &amp;nErr, msg, sizeof(msg), &amp;cbmsg) == SQL_SUCCESS) {
      sprintf_s((char *)szData, MAX_DATA, "Error:\nSQLSTATE=%s, Native error=%ld, msg='%s'", 
         szSQLSTATE, nErr, msg);

      MessageBox(NULL, (const char *)szData, "ODBC Error", MB_OK);
   }
}

int main (){
   // Declare an instance of the direxec object.
   direxec x;

   // Allocate handles and connect.
   x.sqlconn();

   // Execute SQL command "SELECT last_name FROM employee".
   x.sqlexec((UCHAR FAR *)"SELECT last_name FROM employee");

   // Free handles, and disconnect.
   x.sqldisconn();

   // Return success code; example executed successfully.
   return (TRUE);
}</code>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>