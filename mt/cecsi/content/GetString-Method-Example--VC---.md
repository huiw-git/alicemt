---
title: "GetString Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4daa93aa-9727-4d1c-886a-e9d22017a1ea
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
# GetString Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString</legacyLink> method.</para>
    <para>Assume you are debugging a data access problem and want a quick, simple way of printing the current contents of a small <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
  </introduction>
  <codeExample>
    <code>// BeginGetString.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include &lt;string.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void GetStringX(void);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

inline char* mygets(char* strDest, int n) {   
   char strExBuff[10];
   char* pstrRet = fgets(strDest, n, stdin);

   if (pstrRet == NULL)
      return NULL;

   // Exhaust the input buffer.
   if (!strrchr(strDest, '\n'))
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
   GetStringX();
   ::CoUninitialize();
}

void GetStringX() {
   HRESULT  hr = S_OK;
  char * token1;

   // Define ADO object pointers.
   // Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRstAuthors = NULL;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source=My_Data_Source; Initial Catalog='pubs'; Integrated Security='SSPI';");
   _bstr_t varOutput; 
   char *strPrompt = "Enter a state (CA, IN, KS, MD, MI, OR, TN, UT): ";
   char strState[3], *pState;

   try {
      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));

      // Open a command object for a stored procedure, 
      // with one parameter.
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));

      printf("%s",strPrompt);
      mygets(strState, 3);

      pState = strtok_s(strState," \t", &amp;token1);

      char strQry[100];
      _snprintf_s(strQry, _countof(strQry), sizeof(strQry)-1, "SELECT au_fname, au_lname, address, city "
         "FROM authors WHERE state = '%s'", pState);
      strQry[sizeof(strQry)-1] = '\0';

      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      pRstAuthors-&gt;Open(strQry, _variant_t((IDispatch*)pConnection, true), 
         adOpenStatic, adLockReadOnly, adCmdText);

      if (pRstAuthors-&gt;RecordCount &gt; 0)  {
         // Use all defaults: get all rows, TAB column delimiter, 
         // CARRIAGE RETURN row delimiter, empty-string null delimiter
         long lRecCount =  pRstAuthors-&gt;RecordCount;
         _bstr_t varTab("\t");
         _bstr_t varRet("\r");
         _bstr_t varNull("");
         varOutput = pRstAuthors-&gt;GetString(adClipString, lRecCount, varTab, varRet, varNull);
         printf("State = '%s'\n", strState);
         printf ("Name            Address            City\n");
         printf ("%s\n", (LPCTSTR)varOutput);
      }
      else
         printf("\nNo rows found for state = '%s'\n", pState);
   } 
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRstAuthors)
      if (pRstAuthors-&gt;State == adStateOpen)
         pRstAuthors-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for (long i = 0 ; i &lt; nCount ; i++) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", pErr-&gt;Number, pErr-&gt;Description);
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
      <code>MD</code>
    </content>
  </section>
  <section>
    <title>Sample Output</title>
    <content>
      <code>Enter a state (CA, IN, KS, MD, MI, OR, TN, UT): State = 'md'
Name            Address            City
Sylvia   Panteley   1956 Arlington Pl.   Rockville</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>