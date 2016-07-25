---
title: "Status Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 194ce221-49bd-4474-ba34-91453d329381
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
# Status Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property to display which records have been modified in a batch operation before a batch update has occurred.</para>
    <code>// BeginStatusCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// This class extracts title_id and type from titles table.
class CTitleRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CTitleRs)
      // Column title_id is the 1st field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szt_Title_id, sizeof(m_szt_Title_id), lt_Title_idStatus, FALSE)

      // Column type is the 3rd field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szt_Type, sizeof(m_szt_Type), lt_TypeStatus, TRUE)

END_ADO_BINDING()

public:
   CHAR m_szt_Title_id[7];
   ULONG lt_Title_idStatus;
   CHAR m_szt_Type[13];
   ULONG lt_TypeStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void StatusX(void);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if(FAILED(CoInitialize(NULL)))
      return -1;

   StatusX();

   ::CoUninitialize();
}

void StatusX() {
   HRESULT  hr = S_OK;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.
   // Initialize pointers on define.
   // These are in the ADODB::  namespace.
    IADORecordBinding *picRs = NULL;   // Interface Pointer Declared
    CTitleRs titlers;   // C++ Class Object
   _RecordsetPtr pRstTitles = NULL;
   LPSTR p_TempStr = NULL;
   char * token1;

   try {
      // Open recordset for batch update
      TESTHR(hr = pRstTitles.CreateInstance(__uuidof(Recordset)));
      pRstTitles-&gt;CursorType = adOpenKeyset;
      pRstTitles-&gt;LockType = adLockBatchOptimistic;
      pRstTitles-&gt;Open ("titles", strCnn, adOpenKeyset, adLockBatchOptimistic, adCmdTable);

      // Open an IADORecordBinding interface pointer which 
      // we will use for binding Recordset to a class.
      TESTHR(hr = pRstTitles-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ class here 
      TESTHR(hr = picRs-&gt;BindToRecordset(&amp;titlers));

      p_TempStr = (LPSTR) malloc(sizeof(titlers.m_szt_Type));

      // Change the type of psychology titles.
      while (!(pRstTitles-&gt;EndOfFile)) {
         // Set the final character of the destination string to NULL.
         p_TempStr[sizeof(titlers.m_szt_Type) - 1] = '\0';

         // The source string will get truncated if its length is 
         // longer than the length of the destination string minus one.
         strncpy_s(p_TempStr,  sizeof(titlers.m_szt_Type), strtok_s(titlers.m_szt_Type, " ", &amp;token1), sizeof(titlers.m_szt_Type) - 1);
         
         // Compare the type of psychology titles
         if (!strcmp(p_TempStr,"psychology"))
               // Copy "self_help" title field
               pRstTitles-&gt;Fields-&gt;GetItem("type")-&gt;Value = (_bstr_t) ("self_help");
         pRstTitles-&gt;MoveNext();
      }

      // Display Title ID and status
      pRstTitles-&gt;MoveFirst();
      while ( !(pRstTitles-&gt;EndOfFile) ) {
         if ( pRstTitles-&gt;Status == adRecModified )
            printf("%s - Modified\n",titlers.lt_Title_idStatus == adFldOK ? titlers.m_szt_Title_id : "&lt;NULL&gt;");
         else
            printf("%s\n",titlers.lt_Title_idStatus == adFldOK ? titlers.m_szt_Title_id : "&lt;NULL&gt;");
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

   // Deallocate the memory
   if (p_TempStr)
      free(p_TempStr);

   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen) {
         // Cancel the update because this is a demonstration.
         pRstTitles-&gt;CancelBatch(adAffectAll);
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
      for (long i = 0; i &lt; nCount; i++) {
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
<link xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status Property (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>