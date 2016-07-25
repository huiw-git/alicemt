---
title: "Clone Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7ac96c1d-d0d8-4bf8-b165-533818d0f590
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
# Clone Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink> method to create copies of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and then lets the user position the record pointer of each copy independently.</para>
    <code>// BeginCloneCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// class extracts only store name  from "stores" table.
class CStores : public CADORecordBinding {
   BEGIN_ADO_BINDING(CStores)

   // Column stor_name is the 1st field in the recordset  
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_szS_stor_name, sizeof(m_szS_stor_name), 
                              lS_stor_nameStatus, FALSE)

   END_ADO_BINDING()

public:
   CHAR m_szS_stor_name[150];
   ULONG lS_stor_nameStatus;
};

// Function Declarations.
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void CloneX();
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
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   CloneX();
   ::CoUninitialize();
}

void CloneX() {
   // Define ADO object pointers, initialize pointers on define.  These are in the ADODB::  namespace.
   _RecordsetPtr  arstStores[3];

   // Define Other Variables
   HRESULT hr = S_OK;
   int intLoop = 0;
   _bstr_t strSQL;
   _bstr_t strMessage;
   _bstr_t strFind;
   int intLoop1 = 0;
   char *tempStr;
   bool boolFlag = TRUE;
   char m_szS_stor_name[150];
   char * token1;

   // Assign SQL statement and connection string to variables.
   strSQL = "SELECT stor_name FROM Stores ORDER BY stor_name";

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try  {
      // Open recordset as a static cursor type recordset.
      arstStores[0].CreateInstance(__uuidof(Recordset));
      arstStores[0]-&gt;CursorType = adOpenStatic;
      arstStores[0]-&gt;LockType = adLockBatchOptimistic;

      TESTHR(arstStores[0]-&gt;Open(strSQL,strCnn, adOpenStatic,
         adLockBatchOptimistic, adCmdText));

      // Create two clones of the original Recordset.
      arstStores[1] = arstStores[0]-&gt;Clone(adLockUnspecified);
      arstStores[2] = arstStores[0]-&gt;Clone(adLockUnspecified);

      while (boolFlag) {
         // Loop through the array so that on each pass, the user is searching a 
         // different copy of the same Recordset.
         for (intLoop = 1; intLoop &lt;= 3 ; intLoop++) {
            // Ask for search string while showing where
            // the current record pointer is for each Recordset.
            printf("Recordsets from stores table:\n"); 

            _bstr_t str1 = arstStores[0]-&gt;Fields-&gt;GetItem("stor_name")-&gt;Value;
            printf("\t1 - Original - Record pointer at %s", (LPCSTR)str1);

            _bstr_t str2 = arstStores[1]-&gt;Fields-&gt;GetItem("stor_name")-&gt;Value;
            printf("\n\t2 - Clone - Record pointer at %s", (LPCSTR)str2);

            _bstr_t str3 = arstStores[2]-&gt;Fields-&gt;GetItem("stor_name")-&gt;Value;
            printf("\n\t3 - Clone - Record pointer at %s", (LPCSTR)str3); 

            printf("\n\nEnter search string for # %d, or press Enter to quit.\n", intLoop);
            mygets(m_szS_stor_name, 150);

            // Trim the String.
            tempStr = strtok_s(m_szS_stor_name, "  \t", &amp;token1);
            strMessage = tempStr;
            if (tempStr == NULL) {
               boolFlag = FALSE;
               break;
            }

            // Find the search string; if there's no
            // match, jump to the last record.
            intLoop1 = intLoop - 1;

            arstStores[intLoop1]-&gt;Filter = "stor_name &gt;= '" + 
               strMessage + "'";

            if (arstStores[intLoop1]-&gt;EndOfFile) {
               arstStores[intLoop1]-&gt;Filter = (long)adFilterNone;
               arstStores[intLoop1]-&gt;MoveLast();
            }
         }
      } // End of While Loop
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _variant_t vtConnect;

      vtConnect = arstStores[0]-&gt;GetActiveConnection();

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

   // Clean up objects before exit.
   if (arstStores[0])
      if (arstStores[0]-&gt;State == adStateOpen)
         arstStores[0]-&gt;Close();
   if (arstStores[1])
      if (arstStores[1]-&gt;State == adStateOpen)
         arstStores[1]-&gt;Close();
   if (arstStores[2])
      if (arstStores[2]-&gt;State == adStateOpen)
         arstStores[2]-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if( (pConnection-&gt;Errors-&gt;Count) &gt; 0)
   {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("Error number: %x\t%s\n", pErr-&gt;Number,
            (LPCSTR) pErr-&gt;Description);
      }
   }
};

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
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>