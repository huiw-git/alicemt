---
title: "GetRows Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08e5c5bf-f7de-4bf9-97a9-f214c128ad8c
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
# GetRows Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink> method to retrieve a specified number of rows from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and to fill an array with the resulting data. The <legacyBold>GetRows</legacyBold> method will return less than the desired number of rows in two cases: either if <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> has been reached, or if <legacyBold>GetRows</legacyBold> tried to retrieve a record that was deleted by another user. The function returns <legacyBold>False</legacyBold> only if the second case occurs. The GetRowsOK function is required for this procedure to run.</para>
  </introduction>
  <codeExample>
    <code>// BeginGetRowsCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;conio.h&gt;

// Function Declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void GetRowsX();
bool GetRowsOK(_RecordsetPtr pRstTemp, int intNumber, _variant_t&amp; avarData);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   GetRowsX();
   ::CoUninitialize();
}

void GetRowsX() {
   HRESULT hr = S_OK;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers, initialize pointers on define. 
   // These are in the ADODB::  namespace.
   _RecordsetPtr pRstEmployees = NULL;

   try  {
      // Open recordset with names and hire dates from employee table.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));

      pRstEmployees-&gt;Open("SELECT fName, lName, hire_date "
         "FROM Employee ORDER BY lName",strCnn, adOpenStatic, adLockReadOnly, adCmdText);

      while (true) {   // continuous loop
         int intLines = 0;

         // Get user input for number of rows.
         printf("Enter number of rows to retrieve (0 to exit): ");
         int intRows;
         scanf_s("%d", &amp;intRows);

         if (intRows &lt;= 0)
            break;

         // If GetRowsOK is successful, print the results,
         // noting if the end of the file was reached.
         _variant_t avarRecords;

         if (GetRowsOK(pRstEmployees, intRows, avarRecords)) {
            long lUbound;
            HRESULT hr = SafeArrayGetUBound(avarRecords.parray, 2, &amp;lUbound);

            if (hr == 0) {
               if (intRows &gt; lUbound + 1) {
                  printf("\n(Not enough records in Recordset to retrieve %d rows)\n", intRows);
               }
            }
            printf("%d record(s) found.\n", lUbound + 1);

            // Print the retrieved data.
            for (int intRecords = 0 ; intRecords &lt; lUbound+1 ; intRecords++) {
               long rgIndices[2];
               rgIndices[0] = 0; 
               rgIndices[1] = intRecords;
               _variant_t result;
               result.vt = VT_BSTR;

               hr = SafeArrayGetElement(avarRecords.parray, rgIndices, &amp;result);

               if (hr == 0)
                  printf("%s ",(LPCSTR)(_bstr_t)result);
               
               rgIndices[0] = 1;

               hr = SafeArrayGetElement(avarRecords.parray, rgIndices, &amp;result);

               if (hr == 0)
                  printf("%s, ",(LPCSTR)(_bstr_t)result);

               rgIndices[0] = 2;

               hr = SafeArrayGetElement(avarRecords.parray, rgIndices, &amp;result);

               if (hr == 0)
                  printf("%s\n", (LPCSTR)(_bstr_t)result);

               intLines ++;

               if (intLines % 10 == 0) {
                  printf("\nPress any key to continue...");
                  _getch();
                  intLines = 0;
                  system("cls");
               }
            }
            printf("\n");
         }
         else {
            // Assume GetRows error caused by another user's data changes, 
            // use Requery to refresh the Recordset and start over.
            printf("GetRows failed--retry?\n");
            char chKey;
            do {
               chKey = _getch();
            } while (toupper(chKey) != 'Y'  &amp;&amp; toupper(chKey) != 'N');

            if (toupper(chKey) == 'Y')
               pRstEmployees-&gt;Requery(adOptionUnspecified);
            else {
               printf("GetRows failed!\n");
               break;
            }
         }

         // Because using GetRows leaves the current record pointer at the last record 
         // accessed, move the pointer back to the beginning of the Recordset before 
         // looping back for another search.
         pRstEmployees-&gt;MoveFirst();
      }
   }  
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstEmployees-&gt;GetActiveConnection();

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

   // Clean up objects before exit.
   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
}

bool GetRowsOK(_RecordsetPtr pRstTemp,int intNumber, _variant_t&amp; avarData) {
   // Store results of GetRows method in array.
   avarData = pRstTemp-&gt;GetRows(intNumber);

   // Return False only if fewer than the desired number of rows were returned, 
   // but not because the end of the Recordset was reached.
   long lUbound;
   HRESULT hr = SafeArrayGetUBound(avarData.parray, 2, &amp;lUbound);   
   if (hr == 0) {
      if ((intNumber &gt; lUbound + 1) &amp;&amp; (!(pRstTemp-&gt;EndOfFile)))
         return false;
      else
         return true;   
   }
   else  {
      printf ("\nUnable to Get the Array's Upper Bound\n");
      return false;
   }
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
    <comments>
      <content>
        <para>Input</para>
        <code>2
0</code>
      </content>
    </comments>
  </codeExample>
  <section>
    <title>Sample Output</title>
    <content>
      <code>2 record(s) found.
Paolo Accorti, 8/27/1992
Pedro Afonso, 12/24/1990</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF, EOF Properties</link>
<link xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>