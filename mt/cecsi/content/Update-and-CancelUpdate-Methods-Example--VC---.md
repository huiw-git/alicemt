---
title: "Update and CancelUpdate Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc59d23a-2f38-42f9-8b65-ed89009e87ec
caps.latest.revision: 10
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
# Update and CancelUpdate Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method in conjunction with the <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method.</para>
    <code>// Update_CancelUpdate_Methods_Sample.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;malloc.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

//This Class extracts only fname,lname from employee table.
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)

      // fname is the 1st field in the recordset    
      ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sze_fname, 
      sizeof(m_sze_fname), le_fnameStatus, FALSE)
      
      // lname is the 2nd field in the recordset.
      ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sze_lname, 
      sizeof(m_sze_lname), le_lnameStatus, FALSE)   

   END_ADO_BINDING()

public:
   CHAR   m_sze_lname[31];
   ULONG   le_lnameStatus;
   CHAR   m_sze_fname[21];
   ULONG   le_fnameStatus;
};

// This Class extracts only empid,fname,lname,from employee table.
class CEmployeeRs1 : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs1)

      // emp_id is the 1st field in the table.    
      ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sze_empid, 
      sizeof(m_sze_empid), le_empidStatus, FALSE)
      
      // fname is the 2nd field in the table.
      ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sze_fname, 
      sizeof(m_sze_fname), le_fnameStatus, FALSE)
      
      // lname is the 4rt field in the table.
      ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_sze_lname, 
      sizeof(m_sze_lname), le_lnameStatus, FALSE)   

   END_ADO_BINDING()
public:
   CHAR   m_sze_empid[10];
   ULONG   le_empidStatus;
   CHAR   m_sze_lname[31];
   ULONG   le_lnameStatus;
   CHAR   m_sze_fname[21];
   ULONG   le_fnameStatus;   
};

// Function Declartion.
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void UpdateX();
void UpdateX2();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   UpdateX();
   UpdateX2();
   ::CoUninitialize();
}

void UpdateX() {
   // Define ADO object pointers.  // Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _RecordsetPtr pRstEmployees = NULL;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   IADORecordBinding *picRs = NULL;   // Interface Pointer declared
   CEmployeeRs emprs;   // C++ Class object.

   try {
      // Open recordset with names from Employee table.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));
      pRstEmployees-&gt;CursorType = adOpenKeyset;
      pRstEmployees-&gt;LockType = adLockOptimistic;
      pRstEmployees-&gt;Open("SELECT fname, lname FROM Employee "
         "ORDER BY lname",strCnn,adOpenKeyset,adLockOptimistic, adCmdText);

      // Store original data.
      _bstr_t strOldFirst = pRstEmployees-&gt;Fields-&gt;GetItem("fname")-&gt;Value;
      _bstr_t strOldLast = pRstEmployees-&gt;Fields-&gt;GetItem("lname")-&gt;Value;

      // Change data in edit buffer.
      pRstEmployees-&gt;Fields-&gt;GetItem("fname")-&gt;Value = (_bstr_t)("Linda");
      pRstEmployees-&gt;Fields-&gt;GetItem("lname")-&gt;Value = (_bstr_t)("Kobara");

      // Show contents of buffer and get user input.
      printf("\n\nEdit in progress:\n\n");

      printf("Original data =  %s %s \n", (LPSTR)strOldFirst, (LPSTR)strOldLast);

      printf("Data in buffer =  %s %s",
         (LPSTR)(_bstr_t) pRstEmployees-&gt;Fields-&gt;GetItem("fname")-&gt;Value,\
         (LPSTR) (_bstr_t) pRstEmployees-&gt;Fields-&gt;GetItem("lname")-&gt;Value);

      // Ask if the User wants to Update
      printf("\n\nUse Update to replace the original data with the"
         " buffered data in the Recordset? (y/n): ");
      int chKey = _getch();

      if ( toupper(chKey) == 'Y' )
         pRstEmployees-&gt;Update();
      else 
         pRstEmployees-&gt;CancelUpdate();

      // Open an IADORecordBinding interface pointer for binding Recordset to a class.
      TESTHR(pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here.
      TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));

      pRstEmployees-&gt;MoveFirst();

      // Show the resulting data.
      printf("\nData in recordset =  %s %s", emprs.le_fnameStatus == 
         adFldOK ? emprs.m_sze_fname : "&lt;NULL&gt;",
         emprs.le_lnameStatus == adFldOK ? 
         emprs.m_sze_lname : "&lt;NULL&gt;");

      // Restore original data because this is a demonstration.
      if ((strcmp((char *)strOldFirst, emprs.m_sze_fname) &amp;&amp; 
         strcmp((char *)strOldLast, emprs.m_sze_lname))) {
         pRstEmployees-&gt;Fields-&gt;GetItem("fname")-&gt;Value = strOldFirst;
         pRstEmployees-&gt;Fields-&gt;GetItem("lname")-&gt;Value = strOldLast;
         pRstEmployees-&gt;Update();
      } 
   }
   catch(_com_error &amp;e) {    
      // Display errors, if any.  Pass connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstEmployees-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
      switch(vtConnect.vt) {
      case VT_BSTR:
         PrintComError(e);
         break;
      case VT_DISPATCH:
         PrintProviderError(vtConnect);
         break;
      default:
         printf("Errors occured.");
         break;
      }
   }

   // Clean up objects before exit.  Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
}

void UpdateX2() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRstEmployees = NULL;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   IADORecordBinding *picRs = NULL;   // Interface Pointer declared
   CEmployeeRs1 emprs;   // C++ Class object.

   try {
      // Open a connection.   
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open(strCnn, "", "", NULL);

      // Open recordset with data from Employee table.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));
      pRstEmployees-&gt;CursorType = adOpenKeyset;
      pRstEmployees-&gt;LockType = adLockOptimistic;
      pRstEmployees-&gt;Open("employee", _variant_t((IDispatch*)pConnection,true),
         adOpenKeyset, adLockOptimistic, adCmdTable);

      pRstEmployees-&gt;AddNew();
      _bstr_t strEmpID = "B-S55555M";
      pRstEmployees-&gt;Fields-&gt;GetItem("emp_id")-&gt;Value = strEmpID;
      pRstEmployees-&gt;Fields-&gt;GetItem("fname")-&gt;Value = (_bstr_t) ("Bill");
      pRstEmployees-&gt;Fields-&gt;GetItem("lname")-&gt;Value = (_bstr_t) ("Sornsin");

      // Show contents of buffer and get user input.
      printf("\n\nAddNew in progress:\n\n");

      printf("Data in buffer = %s ,  %s %s",
         (LPSTR) (_bstr_t) pRstEmployees-&gt;Fields-&gt;GetItem("emp_id")-&gt;Value,
         (LPSTR) (_bstr_t) pRstEmployees-&gt;Fields-&gt;GetItem("fname")-&gt;Value,
         (LPSTR) (_bstr_t) pRstEmployees-&gt;Fields-&gt;GetItem("lname")-&gt;Value);

      printf("\n\nUse Update to save buffer to recordset?(y/n):");
      int chKey = _getch();

      if ( toupper(chKey) == 'Y') {
         pRstEmployees-&gt;Update();

         // Open IADORecordBinding interface pointer for binding Recordset to a class.
         TESTHR(pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

         // Bind the Recordset to a C++ Class here    
         TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));

         // Go to the new record and show the resulting data.
         printf ("\n\nData in recordset =  %s ,  %s %s",
            emprs.le_empidStatus == adFldOK ? 
            emprs.m_sze_empid : "&lt;NULL&gt;",
            emprs.le_fnameStatus == adFldOK ? 
            emprs.m_sze_fname : "&lt;NULL&gt;",
            emprs.le_lnameStatus == adFldOK ? 
            emprs.m_sze_lname : "&lt;NULL&gt;");
      }
      else {
         pRstEmployees-&gt;CancelUpdate();
         printf("\n\nNo new record added.\n");
      }
      // Delete new data because this is a demonstration.
      _bstr_t strSQLDelete("DELETE FROM employee WHERE emp_id = '" + strEmpID + "'");
      pConnection-&gt;Execute(strSQLDelete, NULL, adExecuteNoRecords);
   }

   catch(_com_error &amp;e) {
      // Display errors, if any. Pass connection pointer accessed from the Connection.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.  Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
      }
   }
}

void PrintComError(_com_error &amp;e) {
   _bstr_t bstrSource(e.Source());
   _bstr_t bstrDescription(e.Description());

   // Print Com errors.  
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s\n", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate Method</link>
<link xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>