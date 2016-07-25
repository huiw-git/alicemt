---
title: "Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5321fc0f-cd0c-4e2a-a5bc-0008fba86b59
caps.latest.revision: 11
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
# Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example triggers an error, traps it, and displays the <legacyLink xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description</legacyLink>, <legacyLink xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext</legacyLink>, <legacyLink xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpFile</legacyLink>, <legacyLink xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError</legacyLink>, <legacyLink xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number</legacyLink>, <legacyLink xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source</legacyLink>, and <legacyLink xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState</legacyLink> properties of the resulting <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object.</para>
    <code>// BeginDescriptionCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void DescriptionX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   DescriptionX();
   ::CoUninitialize();
}

void DescriptionX() {
   // Define ADO object pointers. Initialize pointers on define. These are in the ADODB::  namespace
   _ConnectionPtr pConnection = NULL;
   ErrorPtr errorLoop = NULL;

   // Define Other Variables
   HRESULT hr = S_OK;

   try {
      // Intentionally trigger an error.  open connection
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));

      if (FAILED(hr = pConnection-&gt;Open("Nothing", "", "", adConnectUnspecified))) {
         _com_issue_error(hr);
         exit(1);
      }

      // Cleanup object before exit.
      pConnection-&gt;Close();
   }
   catch(_com_error) {
      // Pass a connection pointer.
      PrintProviderError(pConnection);
   }
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Define Other Variables
   HRESULT hr = S_OK;
   _bstr_t strError;
   ErrorPtr pErr = NULL;

   try {
      // Enumerate Errors collection and display properties of each Error object.
      long nCount = pConnection-&gt;Errors-&gt;Count;

      // Collection ranges from 0 to nCount - 1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("Error #%d\n", pErr-&gt;Number);
         printf(" %s\n", (LPCSTR)pErr-&gt;Description);
         printf(" (Source: %s)\n", (LPCSTR)pErr-&gt;Source);
         printf(" (SQL State: %s)\n", (LPCSTR)pErr-&gt;SQLState);
         printf(" (NativeError: %d)\n", (LPCSTR)pErr-&gt;NativeError);

         if ((LPCSTR)pErr-&gt;GetHelpFile() == NULL)
            printf("\tNo Help file available\n");
         else {
            printf("\t(HelpFile: %s\n)" ,pErr-&gt;HelpFile);
            printf("\t(HelpContext: %s\n)" , pErr-&gt;HelpContext);
         }
      }
   }

   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      PrintComError(e);
   }
}

void PrintComError(_com_error &amp;e) {
   // Notify the user of errors if any.
   _bstr_t bstrSource(e.Source());
   _bstr_t bstrDescription(e.Description());

   // Print Com errors.
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description Property</link>
<link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error Object</link>
<link xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext Property</link>
<link xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpFile Property</link>
<link xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError Property</link>
<link xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number Property</link>
<link xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source Property (ADO Error)</link>
<link xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>