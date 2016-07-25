---
title: "UpdateBatch and CancelBatch Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcb1468e-18bb-41b8-8902-6ee05b786eec
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
# UpdateBatch and CancelBatch Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method in conjunction with the <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> method.</para>
    <code>// BeginUpdateBatchCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// class extracts titles and type from Titles table
class CTitleRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CTitleRs)

   // Column title is the 2nd field in the table
   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szt_Title, sizeof(m_szt_Title), lt_TitleStatus, FALSE)

   // Column type is the 3rd field in the table
   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szt_Type, sizeof(m_szt_Type), lt_TypeStatus, TRUE)
   END_ADO_BINDING()

public:
   CHAR m_szt_Title[81];
   ULONG lt_TitleStatus;
   CHAR m_szt_Type[13];
   ULONG lt_TypeStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void UpdateBatchX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   UpdateBatchX();
   ::CoUninitialize();
}

void UpdateBatchX() {
   HRESULT  hr = S_OK;

   // Define ADO object pointers.    // Initialize pointers on define. 
   // These are in the ADODB::  namespace.
   _RecordsetPtr pRstTitles = NULL;
   char * token1;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   IADORecordBinding *picRs = NULL;   // Interface Pointer Declared
   CTitleRs titlers;   // C++ Class Object

   try {
      // Open titles table.
      TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset)));
      pRstTitles-&gt;CursorType = adOpenKeyset;
      pRstTitles-&gt;LockType = adLockBatchOptimistic;
      pRstTitles-&gt;Open ("titles", strCnn, adOpenKeyset, adLockBatchOptimistic, adCmdTable);

      // Open IADORecordBinding interface pointer for binding recordset to a class
      TESTHR(pRstTitles-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Binding the Recordset to a C++ Class
      TESTHR(picRs-&gt;BindToRecordset(&amp;titlers));
      pRstTitles-&gt;MoveFirst();

      // Loop through recordset and ask user if she wants,
      // to change the type for a specified title.
      while (!(pRstTitles-&gt;EndOfFile)) {
         // Compare type with psychology
         if (!strcmp( (char *)strtok_s(titlers.m_szt_Type, " ", &amp;token1), "psychology" )) { 
               printf("\n\nTitle: %s \nChange type to self_help?(y/n):", titlers.m_szt_Title);
               char chKey;
               chKey = _getch();
               if (toupper(chKey) == 'Y') {
                  // Change type to self_help.
                  pRstTitles-&gt;Fields-&gt;GetItem("type")-&gt;Value = (_bstr_t)("self_help");
               }
         }
         pRstTitles-&gt;MoveNext();
      }

      // commit all the changes made above?
      printf("\n\nSave all changes?");
      char chKey;
      chKey = _getch();
      if (toupper(chKey) == 'Y')
         pRstTitles-&gt;UpdateBatch(adAffectAll);
      else
         pRstTitles-&gt;CancelBatch(adAffectAll);

      // Print current data in recordset.
      pRstTitles-&gt;Requery(adOptionUnspecified);

      // Open IADORecordBinding interface pointer for Binding Recordset to a class    
      TESTHR(pRstTitles-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // ReBinding the Recordset to a C++ Class.
      TESTHR(picRs-&gt;BindToRecordset(&amp;titlers));

      // Move to the first record of the title table
      pRstTitles-&gt;MoveFirst();

      system("cls");

      while (!pRstTitles-&gt;EndOfFile) {
         printf("%s -  %s\n",
            titlers.lt_TitleStatus == adFldOK ? 
            titlers.m_szt_Title :"&lt;NULL&gt;",
            titlers.lt_TypeStatus == adFldOK ? 
            titlers.m_szt_Type :"&lt;NULL&gt;");
         pRstTitles-&gt;MoveNext();
      }

      pRstTitles-&gt;MoveFirst();

      // Restore original data because this is demonstration.
      while (!(pRstTitles-&gt;EndOfFile)) {
         // Compare type with psychology
         if (!strcmp( (char *)strtok_s(titlers.m_szt_Type, " ", &amp;token1), "self_help" )) {
            // Change type to psychology.
            pRstTitles-&gt;Fields-&gt;GetItem("type")-&gt;Value = (_bstr_t)("psychology");
         }
         pRstTitles-&gt;MoveNext();
      }
   }
   catch (_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstTitles-&gt;GetActiveConnection();

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

   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen) {
         pRstTitles-&gt;UpdateBatch(adAffectAll);
         pRstTitles-&gt;Close();
      }
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
<link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
<link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>