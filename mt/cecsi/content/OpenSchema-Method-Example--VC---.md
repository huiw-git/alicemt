---
title: "OpenSchema Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f3da460-0f49-41e0-999d-a754ec1d887e
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
# OpenSchema Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema</legacyLink> method to display the name and type of each table in the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database.</para>
    <code>// OpenSchemaMethodExample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;oleauto.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void OpenSchemaX();
void OpenSchemaX2();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   OpenSchemaX();
   OpenSchemaX2();
   ::CoUninitialize();
}

void OpenSchemaX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRstSchema = NULL;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      pRstSchema = pConnection-&gt;OpenSchema(adSchemaTables);

      while ( !(pRstSchema-&gt;EndOfFile) ) {
         _bstr_t table_name = pRstSchema-&gt;Fields-&gt;GetItem("TABLE_NAME")-&gt;Value;

         printf("Table Name: %s\n",(LPCSTR) table_name);

         _bstr_t table_type = pRstSchema-&gt;Fields-&gt;GetItem("TABLE_TYPE")-&gt;Value;

         printf("Table type: %s\n\n",(LPCSTR) table_type);

         pRstSchema-&gt;MoveNext();         
      }
   }
   catch (_com_error &amp;e) {
      // Display errors, if any. Pass connection pointer accessed from the Connection.        
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRstSchema)
      if (pRstSchema-&gt;State == adStateOpen)
         pRstSchema-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

void OpenSchemaX2() {
   // Define ADO object pointers. Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _ConnectionPtr pConnection2 = NULL;
   _RecordsetPtr pRstSchema = NULL;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open connection.
      TESTHR(pConnection2.CreateInstance(__uuidof(Connection)));
      pConnection2-&gt;Open (strCnn, "", "", adConnectUnspecified);

      // Create a safearray which takes four elements,and pass it as 
      // 2nd parameter in OpenSchema method.
      SAFEARRAY FAR* psa = NULL;
      SAFEARRAYBOUND rgsabound;
      _variant_t  var;
      _variant_t  Array;
      rgsabound.lLbound = 0;
      rgsabound.cElements = 4;
      psa = SafeArrayCreate(VT_VARIANT, 1, &amp;rgsabound);
      var.vt = VT_EMPTY;

      long ix;
      ix = 0;
      SafeArrayPutElement(psa, &amp;ix, &amp;var);

      ix= 1;
      SafeArrayPutElement(psa, &amp;ix, &amp;var);

      ix = 2;
      SafeArrayPutElement(psa, &amp;ix, &amp;var);

      var.vt = VT_BSTR;
      char * s1 = "VIEW";
      _bstr_t str = s1;
      var.bstrVal = str;

      ix = 3;
      SafeArrayPutElement(psa, &amp;ix, &amp;var);

      Array.vt = VT_ARRAY|VT_VARIANT;
      Array.parray = psa;  

      pRstSchema = pConnection2-&gt;OpenSchema(adSchemaTables,&amp;Array);

      while(!(pRstSchema-&gt;EndOfFile))
      {
         printf("Table Name: %s\n", 
            (LPCSTR) (_bstr_t) pRstSchema-&gt;Fields-&gt;GetItem("TABLE_NAME")-&gt;Value);

         printf("Table type: %s\n\n",
            (LPCSTR) (_bstr_t) pRstSchema-&gt;Fields-&gt;GetItem("TABLE_TYPE")-&gt;Value);

         pRstSchema-&gt;MoveNext();         
      }
   }    // End Try statement.
   catch (_com_error &amp;e) {
      // Display errors, if any. Pass connection pointer accessed from the Connection.
      PrintProviderError(pConnection2);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRstSchema)
      if (pRstSchema-&gt;State == adStateOpen)
         pRstSchema-&gt;Close();
   if (pConnection2)
      if (pConnection2-&gt;State == adStateOpen)
         pConnection2-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
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
  </introduction>
  <relatedTopics>
<link xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>