---
title: "Refresh Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3dc3443b-a1b0-4fbd-908a-6e274dec981c
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
# Refresh Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates using the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method to refresh the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection for a stored procedure <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
  </introduction>
  <codeExample>
    <code>// BeginRefreshCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// Class extracts lname,fname from authors table. 
class CAuthorsRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CAuthorsRs)

   // Column lname is the 2nd field in the recordset
   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_lname, 
                              sizeof(m_szau_lname), lau_lnameStatus, TRUE)

   // Column fname is the 3rd field in the recordset.
   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szau_fname, 
                              sizeof(m_szau_fname), lau_fnameStatus, TRUE)
   
END_ADO_BINDING()

public:
   CHAR m_szau_fname[21];
   ULONG lau_fnameStatus;    
   CHAR m_szau_lname[41];
   ULONG lau_lnameStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void RefreshX();
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

   RefreshX();
   ::CoUninitialize();
}

void RefreshX() {
   HRESULT  hr = S_OK;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.  Initialize pointers on define.  These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _CommandPtr pCmdByRoyalty = NULL;
   _RecordsetPtr pRstByRoyalty = NULL;
   _RecordsetPtr pRstAuthors = NULL;
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared. 
   CAuthorsRs authorsrs;   // C++ class object
   char * token1;

   try {
      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      // Open a command object for a stored procedure, with one parameter.
      TESTHR(pCmdByRoyalty.CreateInstance(__uuidof(Command)));
      pCmdByRoyalty-&gt;ActiveConnection = pConnection;
      pCmdByRoyalty-&gt;CommandText = "byroyalty";
      pCmdByRoyalty-&gt;CommandType = adCmdStoredProc;
      pCmdByRoyalty-&gt;Parameters-&gt;Refresh();

      // Get parameter value and execute the command, storing the results in a recordset.
      char *strRoyalty;
      char strTemp[5];
      do {
         printf("\n\nEnter royalty : ");
         mygets(strTemp, 5);

         strRoyalty = strtok_s(strTemp," \t", &amp;token1);
         if (strRoyalty == NULL) {
            exit(1);
         }

         // if the input is not numeric then notify the user.
         if (!atoi(strRoyalty)) {
            printf("\nExpecting numeric value...");
            continue;
         }
      } while (!atoi(strRoyalty));

      _variant_t vtroyal;
      vtroyal.vt = VT_I2;
      vtroyal.iVal = atoi(strRoyalty);
      _variant_t Index;
      Index.vt = VT_I2;
      Index.iVal = 1;
      pCmdByRoyalty-&gt;GetParameters()-&gt;GetItem(Index)-&gt;PutValue(vtroyal);
      pRstByRoyalty = pCmdByRoyalty-&gt;Execute(NULL,NULL,adCmdStoredProc);

      // Open the Authors table to get author names for display.
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));
      pRstAuthors-&gt;Open ("authors", _variant_t((IDispatch *) pConnection, true),
         adOpenForwardOnly, adLockReadOnly, adCmdTable);

      // Open an IADORecordBinding interface pointer which we'll use for 
      // Binding Recordset to a class.
      TESTHR(pRstAuthors-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here.
      TESTHR(picRs-&gt;BindToRecordset(&amp;authorsrs));

      // Print current data in the recordset,adding 
      // author names from Authors table.
      printf("Authors with %s percent royalty\n\n", strRoyalty);
      while (!(pRstByRoyalty-&gt;EndOfFile)) {
         _bstr_t strAuthorID = pRstByRoyalty-&gt;Fields-&gt;GetItem("au_id")-&gt;Value;

         printf("  %s",(LPCSTR) (_bstr_t) pRstByRoyalty-&gt;Fields-&gt;GetItem("au_id")-&gt;Value);

         pRstAuthors-&gt;Filter = "au_id ='"+strAuthorID+"'";
         printf(", %s %s\n",authorsrs.lau_fnameStatus == adFldOK ? 
            authorsrs.m_szau_fname : "&lt;NULL&gt;",
            authorsrs.lau_lnameStatus == adFldOK ? 
            authorsrs.m_szau_lname : "&lt;NULL&gt;");
         pRstByRoyalty-&gt;MoveNext();
      }
   }
   catch (_com_error &amp;e) {
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   if (pRstByRoyalty)
      if (pRstByRoyalty-&gt;State == adStateOpen)
         pRstByRoyalty-&gt;Close();
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

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
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

   // Print COM errors. 
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
      <code>25</code>
    </content>
  </section>
  <section>
    <title>Sample Output</title>
    <content>
      <code>Authors with 25 percent royalty

  724-80-9391, Stearns MacFeathe
  899-46-2035, Anne Ringer</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>