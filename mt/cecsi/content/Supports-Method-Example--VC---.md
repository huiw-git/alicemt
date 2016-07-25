---
title: "Supports Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e174179-9d95-41b9-b72b-6cdbdca6e255
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
# Supports Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method to display the options supported by a recordset opened with different cursor types. The DisplaySupport function is required for this example to run.</para>
    <code>// SupportsMethodExample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;conio.h&gt;

// Function Declarations.
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };

void SupportsX();
void DisplaySupport(_RecordsetPtr pRstTemp);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;
   SupportsX();
   ::CoUninitialize();
}

void SupportsX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _RecordsetPtr pRstTitles = NULL;

   // Assign connection string to a variable
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open a recordset from Titles table
      TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset)));

      // Fill array with CursorType constants.
      int aintCursorType[4];
      aintCursorType[0] = adOpenForwardOnly;
      aintCursorType[1] = adOpenKeyset;
      aintCursorType[2] = adOpenDynamic;
      aintCursorType[3] = adOpenStatic;

      // Open recordset using each CursorType and optimistic locking.
      // Then call the DisplaySupport procedure to display the supported options.
      for (int intIndex=0 ; intIndex &lt;= 3 ; intIndex++) {
         pRstTitles-&gt;CursorType = (enum CursorTypeEnum)aintCursorType[intIndex];
         pRstTitles-&gt;LockType = adLockOptimistic;

         // Pass the Cursor type and LockType to the Recordset.
         pRstTitles-&gt;Open ("titles", strCnn, 
            (enum CursorTypeEnum)aintCursorType[intIndex], adLockOptimistic, adCmdTable);

         switch(aintCursorType[intIndex]) {
         case adOpenForwardOnly:
            printf("\nForwardOnly cursor supports:\n");
            break;

         case adOpenKeyset:
            printf("\nKeyset cursor supports:\n");
            break;

         case adOpenDynamic:
            printf("\nDynamic cursor supports:\n");
            break;

         case adOpenStatic:
            printf("\nStatic cursor supports:\n");
            break;

         default :
            break;
         }

         DisplaySupport(pRstTitles);
      }
   }
   catch(_com_error &amp;e) {
      // Display errors, if any. Pass connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstTitles-&gt;GetActiveConnection();

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
   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen)
         pRstTitles-&gt;Close();
}

void DisplaySupport (_RecordsetPtr pRstTemp) {
   // Fill array with cursor option constants.
   long  alngConstants[11];
   alngConstants[0] = adAddNew;
   alngConstants[1] = adApproxPosition;
   alngConstants[2] = adBookmark;
   alngConstants[3] = adDelete;
   alngConstants[4] = adFind;
   alngConstants[5] = adHoldRecords;
   alngConstants[6] = adMovePrevious;
   alngConstants[7] = adNotify;
   alngConstants[8] = adResync;
   alngConstants[9] = adUpdate;
   alngConstants[10] = adUpdateBatch;

   for ( int intIndex = 0 ; intIndex &lt;= 10 ; intIndex++ ) {
      VARIANT_BOOL booSupports = pRstTemp-&gt;Supports( (enum CursorOptionEnum)alngConstants[intIndex] );

      if (booSupports) {
         switch(alngConstants[intIndex]) {
         case adAddNew :
            printf("\n  AddNew");
            break;

         case adApproxPosition :
            printf("\n  AbsolutePosition and AbsolutePage");
            break;

         case adBookmark :
            printf("\n  Bookmark");
            break;

         case adDelete :
            printf("\n  Delete");
            break;

         case adFind :
            printf("\n  Find");
            break;

         case adHoldRecords :
            printf("\n  Holding Records");
            break;

         case adMovePrevious :
            printf("\n  MovePrevious and Move");
            break;

         case adNotify :
            printf("\n  Notifications");
            break;

         case adResync :
            printf("\n  Resyncing data");
            break;

         case adUpdate :
            printf("\n  Update");
            break;

         case adUpdateBatch :
            printf("\n  Batch updating");
            break;

         default :
            break;
         }
      }
   }
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0 ) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
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
  </introduction>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>