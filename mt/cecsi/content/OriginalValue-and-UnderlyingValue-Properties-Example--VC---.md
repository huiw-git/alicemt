---
title: "OriginalValue and UnderlyingValue Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5762ad2-f43b-453d-b44a-9c70210eb00f
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
# OriginalValue and UnderlyingValue Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue</legacyLink> and <legacyLink xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue</legacyLink> properties by displaying a message if a record's underlying data has changed during a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> batch update.</para>
  </introduction>
  <codeExample>
    <code>// BeginOriginalValueCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// class extracts title_id and type from titles table
class CTitleRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CTitleRs)

   // Column title_id is the 1st field in the Recordset
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szau_Title_id, sizeof(m_szau_Title_id), lau_Title_idStatus, FALSE)

   // Column type is the 3rd field in the Recordset
   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szau_Type, sizeof(m_szau_Type), lau_TypeStatus, TRUE)

   END_ADO_BINDING()

public:
   CHAR m_szau_Title_id[7];
   ULONG lau_Title_idStatus;
   CHAR m_szau_Type[13];
   ULONG lau_TypeStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void OriginalValueX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   OriginalValueX();
   ::CoUninitialize();
}

void OriginalValueX() {
   // Define ADO object pointers, initialize pointers on define.  These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   FieldPtr pFldType = NULL;
   _RecordsetPtr pRstTitles = NULL;

   // Define string variables.
   _bstr_t strSQLChange("UPDATE Titles SET Type = 'sociology' WHERE Type = 'psychology'");
   _bstr_t strSQLRestore("UPDATE Titles SET Type = 'psychology' WHERE Type = 'sociology'");

   // Define Other Variables
   HRESULT hr = S_OK;
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared
   CTitleRs titlers;   // C++ Class object
   char * token1;

   try {
      _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      // Open Recordset for batch update.
      TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset)));
      pRstTitles-&gt;PutActiveConnection(_variant_t((IDispatch *)pConnection, true));
      pRstTitles-&gt;CursorType = adOpenKeyset;
      pRstTitles-&gt;LockType = adLockBatchOptimistic;

      // Cast connection pointer to IDispatch type; convert to correct variant type.
      pRstTitles-&gt;Open("Titles", _variant_t((IDispatch *)pConnection,true),
         adOpenKeyset, adLockBatchOptimistic, adCmdTable);

      // Open IADORecordBinding interface pointer for Binding Recordset to a class.
      TESTHR(pRstTitles-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here  
      TESTHR(picRs-&gt;BindToRecordset(&amp;titlers));

      // Set field object variable for Type field.
      pFldType = pRstTitles-&gt;Fields-&gt;GetItem("type");

      // Change the type of psychology titles.
      while ( !(pRstTitles-&gt;EndOfFile) ) {
         if (!strcmp(strtok_s((char *)titlers.m_szau_Type, " ", &amp;token1), "psychology"))
            pFldType-&gt;Value = "self_help";
         pRstTitles-&gt;MoveNext();
      }

      // Simulate a change by another user by updating data using a command string.
      pConnection-&gt;Execute(strSQLChange, NULL, 0);

      // Check for changes.
      pRstTitles-&gt;MoveFirst();
      while (!(pRstTitles-&gt;EndOfFile)) {
         if (strcmp(pFldType-&gt;OriginalValue.pcVal, pFldType-&gt;UnderlyingValue.pcVal)) {
            printf("Data has changed!");

            printf("\nTitle ID: %s", titlers.lau_Title_idStatus == 
               adFldOK ? titlers.m_szau_Title_id : "&lt;NULL&gt;");

            printf("\nCurrent Value: %s", (LPCSTR) (_bstr_t) pFldType-&gt;Value);

            printf("\nOriginal Value: %s", (LPCSTR) (_bstr_t) pFldType-&gt;OriginalValue);

            printf("\nUnderlying Value: %s\n\n", (LPCSTR) (_bstr_t) pFldType-&gt;UnderlyingValue);
         }
         pRstTitles-&gt;MoveNext();
      }
   }
   catch (_com_error &amp;e)  {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Connection.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.  Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen) {
         // Cancel the update because this is a demonstration.
         pRstTitles-&gt;CancelBatch(adAffectAll);
         pRstTitles-&gt;Close();
      }
      if (pConnection)
         if (pConnection-&gt;State == adStateOpen) {
            // Restore Original Values.
            pConnection-&gt;Execute(strSQLRestore, NULL, 0);
            pConnection-&gt;Close();
         }
};

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0 ) {
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
    <comments>
      <content>
        <computerOutput>Data has changed!
Title ID: PS1372
Current Value: self_help   
Original Value: psychology  
Underlying Value: sociology   

Data has changed!
Title ID: PS2091
Current Value: self_help   
Original Value: psychology  
Underlying Value: sociology   

Data has changed!
Title ID: PS2106
Current Value: self_help   
Original Value: psychology  
Underlying Value: sociology   

Data has changed!
Title ID: PS3333
Current Value: self_help   
Original Value: psychology  
Underlying Value: sociology   

Data has changed!
Title ID: PS7777
Current Value: self_help   
Original Value: psychology  
Underlying Value: sociology   
</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>