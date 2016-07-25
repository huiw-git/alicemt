---
title: "MarshalOptions Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3b6fc09-ce21-450d-9063-bac505208d31
caps.latest.revision: 11
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
# MarshalOptions Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="390c8abf-133e-40da-8b99-8f748a983e4f">MarshalOptions</legacyLink> property to specify what rows are sent back to the server — All Rows or only Modified Rows.</para>
    <code>// BeginMarshalOptionsCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;conio.h&gt;
#include &lt;malloc.h&gt;
#include "icrsint.h"

// This Class extracts only fname,lname from employees table
class CEmployeeRs : public CADORecordBinding {

   BEGIN_ADO_BINDING(CEmployeeRs)

   // Column fname is the 1st field in the recordset
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szemp_fname, sizeof(m_szemp_fname), lemp_fnameStatus, TRUE)
   
   // Column lname is the 2nd field in the recordset
   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szemp_lname, sizeof(m_szemp_lname), lemp_lnameStatus, TRUE)

   END_ADO_BINDING()

public:
   CHAR m_szemp_fname[21];
   ULONG lemp_fnameStatus;
   CHAR m_szemp_lname[31];
   ULONG lemp_lnameStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void MarshalOptionsX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   MarshalOptionsX();
   ::CoUninitialize();
}

void MarshalOptionsX() {
   // Define string variables
   char * token1;
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.  Initialize pointers on define.  These are in the ADODB::  namespace.
   _RecordsetPtr pRstEmployees = NULL;

   // Define Other Variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared
   CEmployeeRs emprs;   // C++ Class Object
   HRESULT hr = S_OK;
   LPSTR strOldFirst = NULL;
   LPSTR strOldLast = NULL;

   try {            
      // Open recordset with names from Employee table.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));
      pRstEmployees-&gt;CursorType = adOpenKeyset;
      pRstEmployees-&gt;LockType = adLockOptimistic;
      pRstEmployees-&gt;CursorLocation = adUseClient;
      pRstEmployees-&gt;Open("SELECT fname, lname FROM Employee ORDER BY lname", strCnn, 
                           adOpenKeyset, adLockOptimistic, adCmdText);

      // Open an IADORecordBinding interface pointer which 
      // we'll use for Binding Recordset to a class.
      TESTHR(pRstEmployees-&gt;QueryInterface( __uuidof(IADORecordBinding), (LPVOID*)&amp;picRs) );

      // Bind the Recordset to a C++ Class here.
      TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));

      // Store Original Data
      strOldFirst = (LPSTR) malloc(sizeof(emprs.m_szemp_fname));
      strOldLast  = (LPSTR) malloc(sizeof(emprs.m_szemp_lname));

      // Set the final character of the destination string to NULL.
      strOldFirst[sizeof(emprs.m_szemp_fname)-1] = '\0';

      // The source string will get truncated if its length is 
      // longer than the length of the destination string minus one.
      strncpy_s(strOldFirst, sizeof(emprs.m_szemp_lname), strtok_s(emprs.m_szemp_fname, " ", &amp;token1), sizeof(emprs.m_szemp_fname) - 1);

      // Set the final character of the destination string to NULL.
      strOldLast[sizeof(emprs.m_szemp_lname) - 1] = '\0';

      // The source string will get truncated if its length is 
      // longer than the length of the destination string minus one.
      strncpy_s(strOldLast, sizeof(emprs.m_szemp_lname), strtok_s(emprs.m_szemp_lname," ", &amp;token1), sizeof(emprs.m_szemp_lname) - 1);
      
      // Change Data in Edit Buffer.  Set the final character of the destination string to NULL.
      emprs.m_szemp_fname[sizeof(emprs.m_szemp_fname) - 1] = '\0';

      // The source string will be truncated if its length is longer than the length of the destination string minus one.
      strncpy_s(emprs.m_szemp_fname, _countof(emprs.m_szemp_fname), "Linda", sizeof(emprs.m_szemp_fname) -1);

      // Set the final character of the destination string to NULL.
      emprs.m_szemp_lname[sizeof(emprs.m_szemp_lname)-1] = '\0';

      // The source string will be truncated if its length is longer than the destination string minus one.
      strncpy_s(emprs.m_szemp_lname, _countof(emprs.m_szemp_lname), "Kobara", sizeof(emprs.m_szemp_lname) -1);

      // Show contents of buffer and get user input
      printf("Edit in Progress:\n");
      printf("Original Data = %s  %s \n",strOldFirst,strOldLast);
      printf("Data in buffer = %s  %s \n", emprs.lemp_fnameStatus == adFldOK ? emprs.m_szemp_fname : "&lt;NULL&gt;",
                                           emprs.lemp_lnameStatus == adFldOK ? emprs.m_szemp_lname : "&lt;NULL&gt;");
      printf("Use Update to replace the original data with the buffered data in the Recordset?\nEnter (y/n) :?");
      char opt1 = _getch();

      if (toupper(opt1)=='Y') {
         printf("\nWould you like to send all the rows in the recordset back to the server?\nEnter (y/n):");
         char opt2 = _getch();
         if (toupper(opt2) == 'Y') {
            pRstEmployees-&gt;MarshalOptions = adMarshalAll;
            picRs-&gt;Update(&amp;emprs);
         }
      }
      else {
         printf("\nWould you like to send only modified rows back to the server?\nEnter (y/n):");
         char opt3 = _getch();
         if (toupper(opt3) == 'Y') {
            pRstEmployees-&gt;MarshalOptions = adMarshalModifiedOnly;
            picRs-&gt;Update(&amp;emprs);
         }
      }

      // Show the resulting data
      printf("\nData In the Recordset = %s  %s\n",
             emprs.lemp_fnameStatus == adFldOK ? 
             emprs.m_szemp_fname : "&lt;NULL&gt;",
             emprs.lemp_lnameStatus == adFldOK ? 
             emprs.m_szemp_lname : "&lt;NULL&gt;");

      // Restore original data because this is a demonstration  
      if ((strcmp(strOldFirst,emprs.m_szemp_fname)) &amp;&amp; (strcmp(strOldLast, emprs.m_szemp_lname))) {
         // Set the final character of the destination string to NULL.
         emprs.m_szemp_fname[sizeof(emprs.m_szemp_fname)-1] = '\0';

         // The source string will get truncated if its length is 
         // longer than the length of the destination string minus one.
         strncpy_s(emprs.m_szemp_fname, _countof(emprs.m_szemp_fname), strOldFirst, sizeof(emprs.m_szemp_fname)-1);

         // Set the final character of the destination string to NULL.
         emprs.m_szemp_lname[sizeof(emprs.m_szemp_lname)-1] = '\0';

         // The source string will get truncated if its length is 
         // longer than the length of the destination string minus one.
         strncpy_s(emprs.m_szemp_lname, _countof(emprs.m_szemp_lname), strOldLast, sizeof(emprs.m_szemp_lname) -1); 
         picRs-&gt;Update(&amp;emprs);
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
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

   // Clean up objects before exit.
   // Deallocate memory
   if (strOldFirst)
      free(strOldFirst);
   if (strOldLast)
      free(strOldLast);

   // Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();
      
   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();   
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for (long i = 0 ; i &lt; nCount ; i++) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
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
<link xlink:href="390c8abf-133e-40da-8b99-8f748a983e4f">MarshalOptions Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>