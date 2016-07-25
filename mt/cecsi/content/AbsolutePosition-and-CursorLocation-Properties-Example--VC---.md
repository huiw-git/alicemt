---
title: "AbsolutePosition and CursorLocation Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48c07216-d199-4822-89f8-ce928d3d2b74
caps.latest.revision: 12
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
# AbsolutePosition and CursorLocation Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink> property can track the progress of a loop that enumerates all the records of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. It uses the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to enable the <legacyBold>AbsolutePosition</legacyBold> property by setting the cursor to a client cursor.</para>
    <code>// BeginAbsolutePositionCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include "conio.h" 
#include "icrsint.h"

// This class extracts last name.  
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)
      // Column lname is the 4th field in the recordset   
      ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_szau_lname, 
      sizeof(m_szau_lname), lau_lnameStatus, TRUE)
   END_ADO_BINDING()

public:
   CHAR   m_szau_lname[41];
   ULONG  lau_lnameStatus;

};

//Function Declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };

void AbsolutePositionX();
void AbsolutePosition2X();
void PrintProviderError(_ConnectionPtr pConnection);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   AbsolutePositionX();

   // Clear the screen for the next display   
   printf("Press any key to continue...");
   _getch();
   system("cls"); 

   AbsolutePosition2X();

   ::CoUninitialize();
}

void AbsolutePositionX() {
   HRESULT hr = S_OK;  

   // Define ADO object pointers.  // Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _RecordsetPtr pRstEmployees = NULL;

   // Define other variables.  Interface Pointer declared.(VC++ Extensions)
   IADORecordBinding *picRs = NULL;
   CEmployeeRs emprs;   // C++ class object
   _bstr_t strMessage;
   char chKey;

   // Open a recordset using a client cursor for the Employee table.

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open a recordset.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));

      // Use client cursor to enable AbsolutePosition property.
      pRstEmployees-&gt;CursorLocation = adUseClient;

      // Explicitly pass the default Cursor type and LockType to the recordset.
      TESTHR(pRstEmployees-&gt;Open("employee", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable));

      // Open an IADORecordBinding interface pointer for binding the recordset to a class.
      TESTHR(pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

      // Bind the recordset to a C++ class here.   
      TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));

      strMessage= "";

      // Enumerate recordset
      do {
         // Display current record information.
         printf("Employee : %s \n record %ld of %d", 
            emprs.lau_lnameStatus == adFldOK ? 
            emprs.m_szau_lname : "&lt;NULL&gt;",
            pRstEmployees-&gt;AbsolutePosition, 
            pRstEmployees-&gt;RecordCount);

         printf("\nContinue?(y/n)  :");

         do {
            chKey = _getch();
         } while (chKey != 'y' &amp;&amp; chKey !='n');

         // Clear the Screen for the next output   
         system("cls");

         if (chKey == 'n')
            break;

         strMessage = "";   
         pRstEmployees-&gt;MoveNext();   
      } while (!(pRstEmployees-&gt;EndOfFile));
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors, if any.
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

   // Clean up objects before exit.  Release the IADORecordset Interface here. 
   if (picRs)
      picRs-&gt;Release();

   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
}

void AbsolutePosition2X() {
   HRESULT hr = S_OK;  

   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _RecordsetPtr pRstEmployees = NULL;

   // Define Other Variables.  Interface Pointer declared.(VC++ Extensions)
   IADORecordBinding *picRs = NULL;
   CEmployeeRs emprs;   // C++ class object
   _bstr_t strMessage;

   // Open a recordset using a client cursor for the Employee table.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open a recordset.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));

      // Use client cursor to enable Absoluteposition property.
      pRstEmployees-&gt;CursorLocation = adUseClient;

      // Explicitly pass the default Cursor type and LockType to the Recordset.
      TESTHR(pRstEmployees-&gt;Open("employee", strCnn, adOpenStatic, adLockReadOnly, adCmdTable));

      // Open an IADORecordBinding interface pointer for Binding Recordset to a class.
      TESTHR(pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here. 
      TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));

      long lGoToPos = 21;

      pRstEmployees-&gt;AbsolutePosition = (PositionEnum)lGoToPos;

      // Display current record information.
      printf("Employee : %s \n record %ld of %d", 
         emprs.lau_lnameStatus == adFldOK ? emprs.m_szau_lname : "&lt;NULL&gt;", pRstEmployees-&gt;AbsolutePosition, 
         pRstEmployees-&gt;RecordCount);

      printf("\nPress any key to continue:");
      _getch();
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

   // Clean up objects before exit. Release the IADORecordset Interface here.  
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
   long nCount = 0;    
   long i = 0;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
      }
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition Property</link>
<link xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>