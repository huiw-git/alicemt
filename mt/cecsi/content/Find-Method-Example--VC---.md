---
title: "Find Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 594c51cb-1157-4417-802b-d91b875ba020
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
# Find Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method to locate and count the number of business titles in the <legacyBold>Pubs</legacyBold> database. The example assumes the underlying provider does not support similar functionality.</para>
    <code>// BeginFindCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// This Class extracts only titleId from Titles table.
class CTitlesRs : public CADORecordBinding {
BEGIN_ADO_BINDING(CTitlesRs)

   // Column title_id is the first field in the recordset from Titles table.
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szt_titleid, sizeof(m_szt_titleid), lt_titleidStatus, FALSE)

END_ADO_BINDING()

public:
   CHAR m_szt_titleid[150];
   ULONG lt_titleidStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void FindX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;
   FindX();
   ::CoUninitialize();
}

void FindX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRstTitles = NULL;
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared.
   CTitlesRs titlers;   // C++ class object

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      // Open title Table
      TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset)));

      pRstTitles-&gt;Open("SELECT title_id FROM titles", 
         _variant_t((IDispatch *)pConnection), 
         adOpenStatic, adLockReadOnly, adCmdText);

      // The default parameters are sufficient to search forward through a Recordset.

      pRstTitles-&gt;Find ("title_id LIKE 'BU%'", 0, adSearchForward, "");

      // Open an IADORecordBinding interface pointer for Binding Recordset to a class    
      TESTHR(pRstTitles-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here    
      TESTHR(picRs-&gt;BindToRecordset(&amp;titlers));

      // Skip the current record to avoid finding the same row repeatedly. 
      // The bookmark is redundant because Find searches from the current position.
      int count = 0;

      // Continue if last find succeeded.
      while (!(pRstTitles-&gt;EndOfFile)) {
         printf("Title ID: %s\n", titlers.lt_titleidStatus == adFldOK ?
            titlers.m_szt_titleid : "&lt;NULL&gt;");
         count++;   // Count the last title found.

         _variant_t mark = pRstTitles-&gt;Bookmark;   // Note current pos.
         pRstTitles-&gt;Find("title_id LIKE 'BU%'", 1, adSearchForward, mark);
      }
      printf("The number of business titles is %d\n", count);
   }
   catch(_com_error &amp;e) {
      // Display errors, if any. Pass connection pointer accessed from the Recordset.
      PrintProviderError(pConnection);
      PrintComError(e);
   }    

   // Clean up objects before exit. Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen)
         pRstTitles-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0 ) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", pErr-&gt;Number, (LPCSTR)pErr-&gt;Description);
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
<link xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>