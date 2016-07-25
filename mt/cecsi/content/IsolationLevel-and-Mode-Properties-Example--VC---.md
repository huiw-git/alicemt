---
title: "IsolationLevel and Mode Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92ddec5d-e3dc-4e8e-997a-c5417cceab69
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
# IsolationLevel and Mode Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property to open an exclusive connection, and the <legacyLink xlink:href="ea84e4b2-fbf2-4eef-b9ce-796b22e21800">IsolationLevel</legacyLink> property to open a transaction that is conducted in isolation of other transactions.</para>
  </introduction>
  <codeExample>
    <code>// BeginIsolationLevelCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF","EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// This class extracts titles and type from Title table
class CTitleRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CTitleRs)

   // Column title is the 2nd field in the table
    ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szau_Title, sizeof(m_szau_Title), lau_TitleStatus, FALSE)

   // Column type is the 3rd field in the table
   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szau_Type, sizeof(m_szau_Type), lau_TypeStatus, TRUE)
   END_ADO_BINDING()

public:
   CHAR m_szau_Title[81];
   ULONG lau_TitleStatus;
   CHAR m_szau_Type[13];
   ULONG lau_TypeStatus;
};

// Function Declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void IsolationLevelX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   IsolationLevelX();
   
   ::CoUninitialize();
}

void IsolationLevelX() {
   // Define ADO ObjectPointers.  Initialize Pointers on define.  These are in the ADODB :: namespace.
   _RecordsetPtr  pRstTitles  = NULL;
   _ConnectionPtr pConnection = NULL;

   // Define other Variables
   HRESULT hr = S_OK;
   IADORecordBinding *picRs = NULL;   // Interface Pointer Declared
   CTitleRs titlers;   // C++ Class Object
   LPSTR p_TempStr = NULL;
   char * token1;
      
   // Assign Connection String to Variable
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open Connection and Titles Table
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Mode = adModeShareExclusive;
      pConnection-&gt;IsolationLevel = adXactIsolated;
      pConnection-&gt;Open(strCnn,"", "", adConnectUnspecified);

      TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset)));
      pRstTitles-&gt;CursorType = adOpenDynamic;
      pRstTitles-&gt;LockType = adLockPessimistic;

      pRstTitles-&gt;Open("titles", _variant_t((IDispatch*) pConnection, true),
                       adOpenDynamic, adLockPessimistic, adCmdTable);

      pConnection-&gt;BeginTrans();

      // Display Connection Mode
      if (pConnection-&gt;Mode == adModeShareExclusive)
         printf("Connection Mode Is Exclusive");
      else
         printf("Connection Mode Is Not Exclusive");     

      // Display Isolation Level 
      if (pConnection-&gt;IsolationLevel == adXactIsolated)
         printf("\nTransaction is Isolated\n");
      else
         printf("\nTransaction is not Isolated\n");

      // Open an IADORecordBinding interface pointer which we will use for binding Recordset to a class.
      TESTHR(pRstTitles-&gt;QueryInterface( __uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ class here
      TESTHR(picRs-&gt;BindToRecordset(&amp;titlers));

      // Change the type of psychology titles.
      p_TempStr = (LPSTR) malloc(sizeof(titlers.m_szau_Type));

      while (!(pRstTitles-&gt;EndOfFile)) {
         // Set the final character of the destination string to NULL.
         p_TempStr[sizeof(titlers.m_szau_Type) - 1] = '\0';

         // The source string will get truncated if its length is 
         // longer than the length of the destination string minus one.
         strncpy_s(p_TempStr, sizeof(titlers.m_szau_Type), strtok_s(titlers.m_szau_Type, " ", &amp;token1), sizeof(titlers.m_szau_Type) - 1);
         
         // Compare type with psychology
         if (!strcmp(p_TempStr,"psychology")) {
            // Set the final character of the destination string to NULL.
            titlers.m_szau_Type[sizeof(titlers.m_szau_Type) - 1] = '\0';

            // Copy "self_help" title field.  The source string will get truncated if its length is 
            // longer than the length of the destination string minus one.
            strncpy_s(titlers.m_szau_Type, sizeof(titlers.m_szau_Type), "self_help", sizeof(titlers.m_szau_Type) - 1);
            picRs-&gt;Update(&amp;titlers);
         }
         pRstTitles-&gt;MoveNext();
      }

      // Print current data in recordset.
      pRstTitles-&gt;Requery(adOptionUnspecified);

      // Open again IADORecordBinding interface pointer for Binding 
      // Recordset to a class.
      TESTHR(pRstTitles-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // ReBinding the Recordset to a C++ Class
      TESTHR(picRs-&gt;BindToRecordset(&amp;titlers));

      // Move to the first record of the title table
      pRstTitles-&gt;MoveFirst();

      // Clear the screen for the next display
      // system("cls");

      while (!pRstTitles-&gt;EndOfFile) {
         printf("%s -  %s\n",titlers.lau_TitleStatus == adFldOK ? 
            titlers.m_szau_Title :"&lt;NULL&gt;",
            titlers.lau_TypeStatus == adFldOK ? 
            titlers.m_szau_Type :"&lt;NULL&gt;");
         pRstTitles-&gt;MoveNext();
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      PrintProviderError(pConnection);
      PrintComError(e);
   }
   
   // Clean up objects before exit.  Release the IADORecordset Interface here.
   if (picRs)
      picRs-&gt;Release();
      
   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen)
         pRstTitles-&gt;Close();

   if (pConnection)
      if (pConnection-&gt;State == adStateOpen) {
         // Restore Original Data
         pConnection-&gt;RollbackTrans();

         pConnection-&gt;Close();
      }

   // Deallocate the memory
   if (p_TempStr)
      free(p_TempStr);
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object
   // pErr is a record object in the Connection's Error collection
   ErrorPtr pErr = NULL;

   if ((pConnection-&gt;Errors-&gt;Count)&gt;0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;

      // Collection ranges from 0 to nCount-1
      for (long i = 0 ; i &lt; nCount ; i++) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error Number :%x \t %s",pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
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
    <comments>
      <content>
        <computerOutput>Connection Mode Is Exclusive
Transaction is Isolated
The Busy Executive's Database Guide -  business
Cooking with Computers: Surreptitious Balance Sheets -  business
You Can Combat Computer Stress! -  business
Straight Talk About Computers -  business
Silicon Valley Gastronomic Treats -  mod_cook
The Gourmet Microwave -  mod_cook
The Psychology of Computer Cooking -  UNDECIDED
But Is It User Friendly? -  popular_comp
Secrets of Silicon Valley -  popular_comp
Net Etiquette -  popular_comp
Computer Phobic AND Non-Phobic Individuals: Behavior Variations -  self_help
Is Anger the Enemy? -  self_help
Life Without Fear -  self_help
Prolonged Data Deprivation: Four Case Studies -  self_help
Emotional Security: A New Algorithm -  self_help
Onions, Leeks, and Garlic: Cooking Secrets of the Mediterranean -  trad_cook
Fifty Years in Buckingham Palace Kitchens -  trad_cook
Sushi, Anyone? -  trad_cook</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="ea84e4b2-fbf2-4eef-b9ce-796b22e21800">IsolationLevel Property</link>
<link xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>