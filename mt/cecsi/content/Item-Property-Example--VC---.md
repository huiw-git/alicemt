---
title: "Item Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05ae3f5a-a0c1-459d-aa7d-ed7f3b2ecd60
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
# Item Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property accesses members of a collection. The example opens the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database with a parameterized command.</para>
    <para>The parameter in the command issued against the database is accessed from the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object's <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection by index and name. Then the fields of the returned <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> are accessed from that object's <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection by index and name.</para>
    <code>// BeginItemCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void ItemX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   ItemX();
   ::CoUninitialize();
}

void ItemX() {
   HRESULT hr = S_OK;

   // Define ADO object pointers.  Initialize pointers on define.  These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRst = NULL;
   _CommandPtr pCmd = NULL;
   _ParameterPtr pPrm = NULL;
   FieldPtr pFld = NULL;

   // Other Variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");
   _variant_t Column[9];
   _variant_t vIndex;

   try {
      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      TESTHR(pRst.CreateInstance(__uuidof(Recordset)));
      TESTHR(pCmd.CreateInstance(__uuidof(Command)));

      // Set the array with the authors table field (column) names
      Column[0] = "au_id";
      Column[1] = "au_lname";
      Column[2] = "au_fname";
      Column[3] = "phone";
      Column[4] = "address";
      Column[5] = "city";
      Column[6] = "state";
      Column[7] = "zip";
      Column[8] = "contract";

      _bstr_t strText("SELECT * FROM authors WHERE state = ?");
      pCmd-&gt;CommandText = strText;

      pPrm = pCmd-&gt;CreateParameter("ItemXparm", adChar, adParamInput, 2, "CA");
      pCmd-&gt;Parameters-&gt;Append(pPrm);

      pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);
      pCmd-&gt;ActiveConnection = pConnection;

      // Connection and CommandType are omitted because a Command object is provided.
      _variant_t Conn;
      Conn.vt = VT_ERROR;
      Conn.scode = DISP_E_PARAMNOTFOUND;

      pRst-&gt;Open((_variant_t((IDispatch *) pCmd)), Conn, adOpenStatic, adLockReadOnly, -1);

      printf("The Parameters collection accessed by index...\n");

      vIndex = (short) 0;
      pPrm = pCmd-&gt;Parameters-&gt;GetItem(&amp;vIndex);
      printf("Parameter name = '%s', value = '%s'\n",
         (LPCSTR)pPrm-&gt;Name, (LPSTR)(_bstr_t)pPrm-&gt;Value);

      printf("\nThe Parameters collection accessed by name...\n");
      pPrm = pCmd-&gt;Parameters-&gt;Item["ItemXparm"];
      printf("Parameter name = '%s', value = '%s'\n",
         (LPCSTR)pPrm-&gt;Name, (LPSTR)(_bstr_t)pPrm-&gt;Value);

      printf("\nThe Fields collection accessed by index...\n");
      pRst-&gt;MoveFirst();
      long limit = 0;
      limit = ((pRst-&gt;Fields-&gt;Count) - 1);
      int intLineCnt = 8; 
      for (short iIndex = 0 ; iIndex &lt;= limit ; iIndex++) {
         vIndex = iIndex;

         pFld = pRst-&gt;Fields-&gt;GetItem(&amp;vIndex);
         printf("Field %d : Name =  '%s', ", iIndex, (LPCSTR)pFld-&gt;GetName());
         _variant_t FldVal = pFld-&gt;GetValue();  

         // Because Value is the default property of a Property object, the use 
         // of the actual keyword here is optional.
         switch(FldVal.vt) {
         case (VT_BOOL):
            if (FldVal.boolVal)
               printf("Value = 'True'");
            else
               printf("Value = 'False'");
            printf("\n");
            break;
         case (VT_BSTR):
            printf("Value = '%s'",
               (LPCSTR)(_bstr_t)FldVal.bstrVal);
            printf("\n");
            break;
         case (VT_I4):
            printf("Value = '%s'",(LPCSTR)FldVal.iVal);
            printf("\n");
            break;
         case (VT_EMPTY):
            printf("Value = '%s'",(LPCSTR)FldVal.lVal);
            printf("\n");
            break;
         default:
            break;
         }
      }

      printf("\nThe Fields collection accessed by name...\n");
      pRst-&gt;MoveFirst();

      for (int iIndex = 0; iIndex &lt;= 8 ; iIndex++) {
         intLineCnt++;

         pFld = pRst-&gt;Fields-&gt;GetItem(Column[iIndex]);
         printf("Field name = '%s', ", (LPCSTR)pFld-&gt;GetName());
         _variant_t FldVal = pFld-&gt;GetValue();

         // Because Value is the default property of a Property object,
         // the use of the actual keyword here is optional.
         switch(FldVal.vt) {
         case (VT_BOOL):
            if (FldVal.boolVal)
               printf("Value = 'True'");
            else
               printf("Value = 'False'");
            printf("\n");
            break;
         case (VT_BSTR):
            printf("Value = '%s'",
               (LPCSTR)(_bstr_t)FldVal.bstrVal);
            printf("\n");
            break;
         case (VT_I4):
            printf("Value = '%s'", (LPCSTR)FldVal.iVal);
            printf("\n");
            break;
         case (VT_EMPTY):
            printf("Value = '%s'", (LPCSTR)FldVal.lVal);
            printf("\n");
            break;
         default:
            break;
         }
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRst)
      if (pRst-&gt;State == adStateOpen)
         pRst-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
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
         printf("\t Error number: %x\t%s", pErr-&gt;Number, pErr-&gt;Description);
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
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item Property</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>