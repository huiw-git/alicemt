---
title: "Append and CreateParameter Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b57d144c-0a34-49c8-94cf-e5981edfcca6
caps.latest.revision: 13
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
# Append and CreateParameter Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> and <legacyLink xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter</legacyLink> methods to execute a stored procedure with an input parameter.</para>
  </introduction>
  <codeExample>
    <code>// BeginAppendCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include "conio.h"
#include "icrsint.h"

// class extracts only author id,fname,lastname
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)
    
   // Column au_id is the 1st field in the recordset   
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szau_id, sizeof(m_szau_id), lau_idStatus, TRUE)

    ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_lname, sizeof(m_szau_lname), lau_lnameStatus, TRUE)

    ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szau_fname, sizeof(m_szau_fname), lau_fnameStatus, TRUE)
   
END_ADO_BINDING()

public:
   CHAR m_szau_id[20];
   ULONG lau_idStatus;
   CHAR m_szau_fname[40];
   ULONG lau_fnameStatus;
   CHAR   m_szau_lname[40];
   ULONG  lau_lnameStatus;
};

// Function declaration
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void AppendX();
void PrintProviderError(_ConnectionPtr pConnection);

int main() {
   HRESULT hr = S_OK;

   if (FAILED(::CoInitialize(NULL)))
        return -1;

    AppendX();
    ::CoUninitialize(); 
}

void AppendX() {
   HRESULT hr = S_OK;

   // Define ADO object pointers. Initialize pointers on define. These are in the ADODB::  namespace.
   _RecordsetPtr pRstByRoyalty = NULL;
   _RecordsetPtr pRstAuthors = NULL;  
   _CommandPtr pcmdByRoyalty = NULL;
   _ParameterPtr pprmByRoyalty = NULL;
   _ConnectionPtr pConnection = NULL;

   //Define Other variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared.(VC++ Extensions)   
   CEmployeeRs emprs;   // C++ class object    

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   _bstr_t strMessage, strAuthorID;

   int intRoyalty;
   VARIANT vtRoyalty;

   try {
      // Open a Connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      hr = pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);
      pConnection-&gt;CursorLocation = adUseClient;

      // Open Command Object with one Parameter
      TESTHR(pcmdByRoyalty.CreateInstance(__uuidof(Command)));
      pcmdByRoyalty-&gt;CommandText = "byroyalty";
      pcmdByRoyalty-&gt;CommandType = adCmdStoredProc;

      // Get parameter value and append parameter
      printf("Enter Royalty: ");
      scanf_s("%d", &amp;intRoyalty);

      // Define Integer/variant.
      vtRoyalty.vt = VT_I2;
      vtRoyalty.iVal = intRoyalty;
      pprmByRoyalty = pcmdByRoyalty-&gt;CreateParameter("percentage", adInteger, adParamInput, sizeof(int), vtRoyalty);
      pcmdByRoyalty-&gt;Parameters-&gt;Append(pprmByRoyalty);

      pprmByRoyalty-&gt;Value = vtRoyalty;

      // Create Recordset by executing the command
      pcmdByRoyalty-&gt;ActiveConnection = pConnection;
      pRstByRoyalty = pcmdByRoyalty-&gt;Execute(NULL, NULL, adCmdStoredProc);

      // Open the authors table to get author names for display
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));

      // You have to explicitly pass the default Cursor type and LockType to the Recordset here
      hr = pRstAuthors-&gt;Open("authors", _variant_t((IDispatch*)pConnection, true), adOpenForwardOnly, adLockReadOnly, adCmdTable); 

      // Open an IADORecordBinding interface pointer which we'll use for Binding Recordset to a class    
      TESTHR(pRstAuthors-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here    
      TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));

      //Print current data in the recordset, adding author names from author table.
      printf("Authors with %d percent royalty ", intRoyalty);

      while(!(pRstByRoyalty-&gt;EndOfFile)) {
         strAuthorID = pRstByRoyalty-&gt;Fields-&gt;Item["au_id"]-&gt;Value;
         pRstAuthors-&gt;Filter = "au_id = '"+strAuthorID+"'";

         printf("\n"  "%s, %s  %s",emprs.lau_idStatus == adFldOK ? emprs.m_szau_id : "&lt;NULL&gt;",\
            emprs.lau_fnameStatus == adFldOK ? emprs.m_szau_fname : "&lt;NULL&gt;",\
            emprs.lau_lnameStatus == adFldOK ? emprs.m_szau_lname : "&lt;NULL&gt;");

         pRstByRoyalty-&gt;MoveNext(); 
      }
   }
   catch(_com_error &amp;e) {
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());
      PrintProviderError(pConnection);
      printf("\n Source : %s \n Description : %s \n", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }

   // Clean up objects before exit.  Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

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
    long nCount = 0;
    long i = 0;

    if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
        nCount = pConnection-&gt;Errors-&gt;Count;
        // Collection ranges from 0 to nCount -1.
        for (i = 0 ; i &lt; nCount ; i++) {
            pErr = pConnection-&gt;Errors-&gt;GetItem(i);
            printf("Error number: %x\n Error Description: %s\n", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
        }
    }
}</code>
    <comments>
      <content>
        <para>Input</para>
        <code>25</code>
      </content>
    </comments>
  </codeExample>
  <section>
    <title>Sample Output</title>
    <content>
      <code>Authors with 25 percent royalty
724-80-9391, Stearns  MacFeather
899-46-2035, Anne  Ringer</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
<link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>