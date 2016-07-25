---
title: "Move Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e08af60-f668-4092-8b6a-9e8b6db90448
caps.latest.revision: 14
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
# Move Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink> method to position the record pointer based on user input.</para>
  </introduction>
  <codeExample>
    <code>// BeginMoveCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;stdlib.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// This Class extracts fname, lname, city and state from the "authors" table.
class CAuthorsRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CAuthorsRs)

   // Column au_id is the 1st field in the recordset   
   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_au_fname, sizeof(m_au_fname), lemp_fnameStatus, TRUE)
   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_au_lname, sizeof(m_au_lname), lemp_lnameStatus, TRUE)
   ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_au_city, sizeof(m_au_city), lemp_cityStatus, TRUE)
   ADO_VARIABLE_LENGTH_ENTRY2(5, adChar, m_au_state, sizeof(m_au_state), lemp_stateStatus, TRUE)
   END_ADO_BINDING()

public:
   char m_au_fname[21];
   ULONG lemp_fnameStatus;
   char m_au_lname[41];
   ULONG lemp_lnameStatus;
   char m_au_city[21];
   ULONG lemp_cityStatus;
   char m_au_state[3];
   ULONG lemp_stateStatus;
};

// Function Declaration.
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void MoveX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

inline char* mygets(char* strDest, int n) {   
   char strExBuff[10];
   char* pstrRet = fgets(strDest, n, stdin);

   if (pstrRet == NULL)
      return NULL;

   if (!strrchr(strDest, '\n'))
      // Exhaust the input buffer.
      do {
         fgets(strExBuff, sizeof(strExBuff), stdin);
      } while (!strrchr(strExBuff, '\n'));
   else
      // Replace '\n' with '\0'
      strDest[strrchr(strDest, '\n') - strDest] = '\0';

   return pstrRet;
}

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   MoveX();
   ::CoUninitialize();
}

void MoveX() {
   // Define ADO object pointers.  Initialize pointers on define.  These are in the ADODB::  namespace.
   _RecordsetPtr pRstAuthors = NULL;
   char *token1;

   // Define Other Variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared  
   CAuthorsRs authorsrs;   // C++ class object
   HRESULT hr = S_OK;

   // Open Authors table
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open recordset from Authors table.
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));

      pRstAuthors-&gt;CursorType = adOpenStatic;
      // Use client cursor to allow use of AbsolutePosition property.
      pRstAuthors-&gt;CursorLocation = adUseClient;

      pRstAuthors-&gt;Open("SELECT au_id, au_fname, au_lname, city, "
         "state FROM Authors ORDER BY au_lname", strCnn, adOpenStatic, adLockReadOnly, adCmdText);

      // Open an IADORecordBinding interface pointer which we'll use 
      // for Binding Recordset to a class.
      TESTHR(pRstAuthors-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here.
      TESTHR(picRs-&gt;BindToRecordset(&amp;authorsrs));

      pRstAuthors-&gt;MoveFirst();

      char * strMove;
      char strTemp[5];
      while (true) {
         // Display information about current record and ask how many records to move.
         printf("Record %ld of %d\n", pRstAuthors-&gt;AbsolutePosition, pRstAuthors-&gt;RecordCount);
         printf("Author: %s %s\n", 
            authorsrs.lemp_fnameStatus == adFldOK ? 
            authorsrs.m_au_fname : "&lt;NULL&gt;", 
            authorsrs.lemp_lnameStatus == adFldOK ? 
            authorsrs.m_au_lname : "&lt;NULL&gt;");
         printf("Location: %s, %s\n\n", 
            authorsrs.lemp_cityStatus == adFldOK ? 
            authorsrs.m_au_city : "&lt;NULL&gt;", 
            authorsrs.lemp_stateStatus == adFldOK ? 
            authorsrs.m_au_state : "&lt;NULL&gt;");

         printf("Enter number of records to Move \n(positive or negative, 0 (zero) to quit): ");
         mygets(strTemp, 5);

         strMove = strtok_s(strTemp, "\t", &amp;token1);

         if (strMove == NULL || *strMove == '0')
            break;

         // if the input is not numeric then notify the user.
         if (!atol(strMove)) {
            printf("Expecting numeric value...\n");
            continue;
         }

         // Store bookmark in case the Move goes too far forward or backward.
         _variant_t varBookmark = pRstAuthors-&gt;Bookmark;

         // Move method requires parameter of data type Long.
         long lngMove = atol(strMove);

         pRstAuthors-&gt;Move(lngMove);

         // Trap for BOF or EOF.
         if (pRstAuthors-&gt;BOF) {
            printf("Too far backward! Returning to current record.\n");
            pRstAuthors-&gt;Bookmark = varBookmark;
         }

         if (pRstAuthors-&gt;EndOfFile) {
            printf("Too far forward! Returning to current record.\n");
            pRstAuthors-&gt;Bookmark = varBookmark;
         }
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstAuthors-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
      switch (vtConnect.vt) {
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

   if (pRstAuthors)
      if (pRstAuthors-&gt;State == adStateOpen)
         pRstAuthors-&gt;Close();

}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr  pErr  = NULL;

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
  </codeExample>
  <section>
    <title>Sample Input</title>
    <content>
      <code>1
0</code>
    </content>
  </section>
  <section>
    <title>Sample Output</title>
    <content>
      <code>Record 1 of 23
Author: Abraham Bennet
Location: Berkeley, CA

Enter number of records to Move 
(positive or negative, Enter to quit): Record 2 of 23
Author: Reginald Blotchet-Halls
Location: Corvallis, OR

Enter number of records to Move 
(positive or negative, Enter to quit):</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>