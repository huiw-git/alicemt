---
title: "ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d9917c4-9ef0-4d7a-b4ce-4f1fa6ce1817
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
# ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink>, <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink>, <legacyLink xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout</legacyLink>, <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink>, <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink>, and <legacyLink xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction</legacyLink> properties to execute a stored procedure.</para>
  </introduction>
  <codeExample>
    <code>// BeginActiveConnectionCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#define TESTHR(x) if FAILED(x) _com_issue_error(x)

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include "conio.h"
#include "icrsint.h"

// class extracts  fname,lastname
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)

   // Column au_id is the 1st field in the recordset   
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szau_id, sizeof(m_szau_id), 
                              lau_idStatus, TRUE)

   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_lname, sizeof(m_szau_lname), 
                              lau_lnameStatus, TRUE)

   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szau_fname, sizeof(m_szau_fname), 
                              lau_fnameStatus, TRUE)

   END_ADO_BINDING()

public:
   CHAR m_szau_id[20];
   ULONG lau_idStatus;
   CHAR m_szau_fname[40];
   ULONG lau_fnameStatus;
   CHAR m_szau_lname[40];
   ULONG lau_lnameStatus;
};

// Function declaration
void ActiveConnectionX();
void PrintProviderError(_ConnectionPtr pConnection);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   ActiveConnectionX();
   ::CoUninitialize();
}

void ActiveConnectionX() {
   HRESULT hr = S_OK;  

   // Define ADO object pointers, initialize pointers on define. These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _CommandPtr pCmdByRoyalty = NULL;
   _RecordsetPtr pRstByRoyalty = NULL;
   _RecordsetPtr pRstAuthors = NULL;
   _ParameterPtr pPrmByRoyalty = NULL;

   // Define Other variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared.(VC++ Extensions)  TCS(SPA)
   CEmployeeRs emprs;   // C++ class object  TCS(SPA)
   _bstr_t strAuthorId;
   int intRoyalty;
   VARIANT vtroyal;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Define a command object for a stored procedure. 
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      hr = pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);

      TESTHR(pCmdByRoyalty.CreateInstance(__uuidof(Command)));

      pCmdByRoyalty-&gt;ActiveConnection = pConnection;
      pCmdByRoyalty-&gt;CommandText = "byRoyalty";
      pCmdByRoyalty-&gt;CommandType = adCmdStoredProc;
      pCmdByRoyalty-&gt;CommandTimeout = 15;

      // Define stored procedure's input parameter. 
      printf("Enter Royalty :  ");
      scanf_s("%d",&amp;intRoyalty);

      // Assign Integer value 
      vtroyal.vt = VT_I2;
      vtroyal.iVal = intRoyalty;

      TESTHR(pPrmByRoyalty.CreateInstance(__uuidof(Parameter)));
      pPrmByRoyalty-&gt;Type = adInteger;
      pPrmByRoyalty-&gt;Size = 3;
      pPrmByRoyalty-&gt;Direction = adParamInput;
      pPrmByRoyalty-&gt;Value = vtroyal;
      pCmdByRoyalty-&gt;Parameters-&gt;Append(pPrmByRoyalty);

      // Create a recordset by executing a command.
      pRstByRoyalty = pCmdByRoyalty-&gt;Execute(NULL,NULL,adCmdStoredProc); 

      // Open the authors table to get author names for display. 
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));
      hr = pRstAuthors-&gt;Open("authors", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);

      // Open an IADORecordBinding interface pointer which we'll use for Binding Recordset to a class
      TESTHR(pRstAuthors-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here
      TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));

      // Print current data in the recordset ,adding author names from author table. 
      printf("Authors With  %d  Percent Royalty", intRoyalty);

      while (!(pRstByRoyalty-&gt;EndOfFile)) {
         strAuthorId = pRstByRoyalty-&gt;Fields-&gt;Item["au_id"]-&gt;Value;
         pRstAuthors-&gt;Filter = "au_id = '" + strAuthorId + "'";

         printf("\n\t%s, %s %s",emprs.lau_idStatus == adFldOK ? emprs.m_szau_id : "&lt;NULL&gt;",\
            emprs.lau_fnameStatus == adFldOK ? emprs.m_szau_fname : "&lt;NULL&gt;",\
            emprs.lau_lnameStatus == adFldOK ? emprs.m_szau_lname : "&lt;NULL&gt;");

         pRstByRoyalty-&gt;MoveNext(); 
      }

   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      PrintProviderError(pConnection);
      printf("Source : %s \n Description : %s \n", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }


   // Clean up objects before exit. Release the IADORecordset Interface here
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
         printf("Error number: %x\t%s", pErr-&gt;Number, (LPCSTR)pErr-&gt;Description);
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
      <code>Authors With  25  Percent Royalty
        724-80-9391, Stearns MacFeather
        899-46-2035, Anne Ringer</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection Property</link>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout Property</link>
<link xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType Property</link>
<link xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction Property</link>
<link xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>