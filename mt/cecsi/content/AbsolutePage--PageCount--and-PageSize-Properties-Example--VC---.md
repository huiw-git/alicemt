---
title: "AbsolutePage, PageCount, and PageSize Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38ca4e1b-c109-4fba-b590-bdd6994f770e
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
# AbsolutePage, PageCount, and PageSize Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink>, <legacyLink xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount</legacyLink>, and <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink> properties to display names and hire dates from the <legacyBold><legacyItalic>Employee</legacyItalic></legacyBold> table, five records at a time.</para>
    <code>// BeginAbsolutePageCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include "conio.h"
#include "icrsint.h"

// This Class extracts only fname,lastname and hire_date
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)

      // Column fname is the 2nd field in the table   
      ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_fname, 
      sizeof(m_szau_fname), lau_fnameStatus, FALSE)

      ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_szau_lname, 
      sizeof(m_szau_lname), lau_lnameStatus, TRUE)

      ADO_VARIABLE_LENGTH_ENTRY2(8, adVarChar, m_szau_hiredate, 
      sizeof(m_szau_hiredate), lau_hiredateStatus, TRUE)

   END_ADO_BINDING()

public:
   CHAR   m_szau_lname[41];
   ULONG  lau_lnameStatus;
   CHAR   m_szau_fname[41];
   ULONG  lau_fnameStatus;
   CHAR   m_szau_hiredate[40];
   ULONG  lau_hiredateStatus;

};

// Function Declarations.
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void AbsolutePageX();
void PrintProviderError(_ConnectionPtr pConnection); 

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   AbsolutePageX();
   ::CoUninitialize();
}

void AbsolutePageX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _RecordsetPtr pRstEmployees = NULL;

   // Define Other Variables.    Interface Pointer declared.(VC++ Extensions)
   IADORecordBinding *picRs = NULL;
   CEmployeeRs emprs;   // C++ class object 
   HRESULT hr = S_OK;
   _bstr_t strMessage;

   // Open a recordset using a Client Cursor for the Employee Table
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open a recordset.
      TESTHR(hr = pRstEmployees.CreateInstance(__uuidof(Recordset)));

      // Use client cursor to enable Absoluteposition property.
      pRstEmployees-&gt;CursorLocation = adUseClient;

      // Explicitly pass the default Cursor type  and LockType to the Recordset here 
      TESTHR(hr = pRstEmployees-&gt;Open("employee", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable));

      // Open an IADORecordBinding interface pointer for Binding Recordset to a class    
      TESTHR(hr = pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here    
      TESTHR(hr = picRs-&gt;BindToRecordset(&amp;emprs));

      // Display Names and hire dates, five records at a time
      pRstEmployees-&gt;PageSize = 5;

      int intPageCount = pRstEmployees-&gt;PageCount;

      for (int intPage = 1 ; intPage &lt;= intPageCount ; intPage++ ) {
         pRstEmployees-&gt;put_AbsolutePage((enum PositionEnum)intPage);
         strMessage = "";

         for ( int intRecord = 1 ; intRecord &lt;= pRstEmployees-&gt;PageSize ; intRecord++ ) {
            printf("\t%s %s %.10s\n", 
               emprs.lau_fnameStatus == adFldOK ? 
               emprs.m_szau_fname : "&lt;NULL&gt;",
               emprs.lau_lnameStatus == adFldOK ? 
               emprs.m_szau_lname : "&lt;NULL&gt;",
               emprs.lau_hiredateStatus == adFldOK ? 
               emprs.m_szau_hiredate : "&lt;NULL&gt;");

            pRstEmployees-&gt;MoveNext();

            if (pRstEmployees-&gt;EndOfFile)
               break;
         }
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _variant_t vtConnect = pRstEmployees-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
      switch(vtConnect.vt) {
      case VT_BSTR:
         printf("Error:\n");
         printf("Code = %08lx\n", e.Error());
         printf("Message = %s\n", e.ErrorMessage());
         printf("Source = %s\n", (LPCSTR) e.Source());
         printf("Description = %s\n", (LPCSTR) e.Description());
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

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      printf("Error:\n");
      for ( long iError = 0 ; iError &lt; nCount ; iError++) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(iError);
         printf("\t Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
      }
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage Property</link>
<link xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount Property</link>
<link xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>