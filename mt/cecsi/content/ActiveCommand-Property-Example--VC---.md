---
title: "ActiveCommand Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8269ea29-912a-4d20-9360-f48b3746081f
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
# ActiveCommand Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand</legacyLink> property.</para>
    <para>A subroutine is given a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object whose <legacyBold>ActiveCommand</legacyBold> property is used to display the command text and parameter that created the <legacyBold>Recordset</legacyBold>.</para>
  </introduction>
  <codeExample>
    <code>// BeginActiveCommandCpp.cpp
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
void ActiveCommandX();
void ActiveCommandXprint(_RecordsetPtr pRst);
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

   ActiveCommandX();
   ::CoUninitialize();
}

void ActiveCommandX() {
   HRESULT hr = S_OK;
   char * token1;

   // Define ADO object pointers, initialize pointers on define.  These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _CommandPtr pCmd = NULL;
   _RecordsetPtr pRstAuthors = NULL;

   // Definitions of other variables
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");
   _bstr_t strPrompt;
   _bstr_t strName;
   CHAR strcharName[50];

   try {
      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));
      TESTHR(pCmd.CreateInstance(__uuidof(Command)));

      printf ("ActiveCommandX Example\n\n");
      strPrompt = "Enter an author's name (e.g., Ringer): ";
      printf(strPrompt);
      mygets(strcharName, 50);
      char *tempStr = strtok_s(strcharName, " \t", &amp;token1);
      strName = tempStr;

      pCmd-&gt;CommandText = "SELECT * FROM authors WHERE au_lname = ?";
      pCmd-&gt;Parameters-&gt;Append(pCmd-&gt;CreateParameter("LastName", adChar, adParamInput, 20, strName));

      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);
      pCmd-&gt;PutActiveConnection(_variant_t((IDispatch*)pConnection));
      pRstAuthors = pCmd-&gt;Execute(NULL, NULL, adCmdText);
      ActiveCommandXprint(pRstAuthors);
   }    // End Try statement.
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

void ActiveCommandXprint(_RecordsetPtr pRst = NULL) {
   // Varible Declaraion &amp; initialization
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared. 
   CAuthorsRs autrs;   // C++ class object
   _bstr_t strName;


   // Open an IADORecordBinding interface pointer which 
   // we'll use for Binding Recordset to a class
   TESTHR(pRst-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

   // Bind the Recordset to a C++ Class here
   TESTHR(picRs-&gt;BindToRecordset(&amp;autrs));

   strName = ((_CommandPtr)pRst-&gt;GetActiveCommand())-&gt;GetParameters()-&gt;GetItem("LastName")-&gt;Value;
   printf("Command text = '%s'\n", (LPCSTR)((_CommandPtr)pRst-&gt;GetActiveCommand())-&gt;CommandText);
   printf("Parameter = '%s'\n", (LPCSTR)strName);

   if (pRst-&gt;BOF)
      printf("Name = '%s'not found.", (LPCSTR)strName);
   else {

      printf ("Name = '%s  %s'",
         autrs.lau_fnameStatus == adFldOK ? autrs.m_szau_fname : "&lt;NULL&gt;",
         autrs.lau_lnameStatus == adFldOK ? autrs.m_szau_lname : "&lt;NULL&gt;");
   }

   // Release IADORecordset Interface    
   if (picRs)
      picRs-&gt;Release();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;
   long nCount = 0;    
   long i = 0;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to (nCount - 1)
      for ( i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR)pErr-&gt;Description);
      }
   }
}

void PrintComError(_com_error &amp;e) {
   _bstr_t bstrSource(e.Source());
   _bstr_t bstrDescription(e.Description());

   // Print Com errors
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
      <code>Ringer</code>
    </content>
  </section>
  <section>
    <title>Sample Output</title>
    <content>
      <code>Command text = 'SELECT * FROM authors WHERE au_lname = ?'
Parameter = 'Ringer'
Name = 'Anne  Ringer'</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>