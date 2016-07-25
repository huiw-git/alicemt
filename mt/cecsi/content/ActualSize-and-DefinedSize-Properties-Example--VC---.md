---
title: "ActualSize and DefinedSize Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05f7cc97-b806-41d2-939d-a955d10844c4
caps.latest.revision: 10
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
# ActualSize and DefinedSize Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize</legacyLink> and <legacyLink xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize</legacyLink> properties to display the defined size and actual size of a field.</para>
  </introduction>
  <codeExample>
    <code>// BeginActualSizeCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include "conio.h" 

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void ActualSizeX();
void PrintProviderError(_ConnectionPtr pConnection);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;
   ActualSizeX();
   ::CoUninitialize();
}

void ActualSizeX() {
   HRESULT hr = S_OK;

   // Define ADO object pointers. Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _RecordsetPtr pRstStores = NULL;

   // Define Other variables
   _bstr_t strMessage;
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open a recordset for the stores table.
      TESTHR(pRstStores.CreateInstance(__uuidof(Recordset)));

      // You have to explicitly pass the Cursor type and LockType to the Recordset here.
      hr = pRstStores-&gt;Open("stores", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);

      // Loop through the recordset displaying the contents of the stor_name field, 
      // the field's defined size, and its actual size.
      pRstStores-&gt;MoveFirst();

      while (!(pRstStores-&gt;EndOfFile)) {
         strMessage = "Store Name: ";
         strMessage += (_bstr_t)pRstStores-&gt;Fields-&gt;Item["stor_name"]-&gt;Value + "\n";
         strMessage += "Defined Size: "; 
         strMessage += (_bstr_t)pRstStores-&gt;Fields-&gt;Item["stor_name"]-&gt;DefinedSize + "\n";
         strMessage += "Actual Size: ";
         strMessage += (_bstr_t) pRstStores-&gt;Fields-&gt;Item["stor_name"]-&gt;ActualSize + "\n"; 

         printf("%s\n",(LPCSTR)strMessage);
         pRstStores-&gt;MoveNext();
      }
   }
   catch(_com_error &amp;e) {
      _variant_t vtConnect = pRstStores-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
      switch(vtConnect.vt) {
         case VT_BSTR:
            printf("Error:\n");
            printf("Code = %08lx\n", e.Error());
            printf("Message = %s\n", e.ErrorMessage());
            printf("Source = %s\n", (LPCSTR) e.Source());
            printf("Description = %s\n", (LPCSTR) e.Description());
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
   if (pRstStores)
      if (pRstStores-&gt;State == adStateOpen)
         pRstStores-&gt;Close();
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
         printf("\t Error number: %x\t%s", pErr-&gt;Number,(LPCSTR ) pErr-&gt;Description);
      }
   }
}</code>
    <comments>
      <content>
        <computerOutput>Store Name: Eric the Read Books
Defined Size: 40
Actual Size: 19

Store Name: Barnum's
Defined Size: 40
Actual Size: 8

Store Name: News &amp; Brews
Defined Size: 40
Actual Size: 12

Store Name: Doc-U-Mat: Quality Laundry and Books
Defined Size: 40
Actual Size: 36

Store Name: Fricative Bookshop
Defined Size: 40
Actual Size: 18

Store Name: Bookbeat
Defined Size: 40
Actual Size: 8
</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize Property</link>
<link xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>