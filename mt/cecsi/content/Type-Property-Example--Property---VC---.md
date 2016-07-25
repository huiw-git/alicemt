---
title: "Type Property Example (Property) (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a4e23508-fbf3-4468-be55-212e7238802b
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
# Type Property Example (Property) (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property. It is a model of a utility for listing the names and types of a collection, like <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink>, <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink>, etc.</para>
    <para>We do not need to open the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to access its <legacyBold>Properties</legacyBold> collection; they come into existence when the <legacyBold>Recordset</legacyBold> object is instantiated. However, setting the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold> adds several dynamic properties to the <legacyBold>Recordset</legacyBold> object's <legacyBold>Properties</legacyBold> collection, making the example a little more interesting. For sake of illustration, we explicitly use the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property to access each <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> object.</para>
    <code>// BeginTypePropertyCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void TypeX();
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   TypeX();
   ::CoUninitialize();
}

void TypeX() {
   // Define ADO object pointers, initialize pointers. These are in the ADODB:: namespace
   _RecordsetPtr pRst = NULL;
   PropertyPtr pProperty = NULL;

   // Define Other Variables
   _bstr_t strMsg;
   _variant_t vIndex;
   int intLineCnt = 0;   

   try {
      TESTHR(pRst.CreateInstance (__uuidof(Recordset)));

      // Set the Recordset Cursor Location
      pRst-&gt;CursorLocation = adUseClient;

      for (short iIndex = 0; iIndex &lt;= (pRst-&gt;Properties-&gt;GetCount() - 1);iIndex++) {
         vIndex = iIndex;
         pProperty = pRst-&gt;Properties-&gt;GetItem(vIndex);

         int propType = (int)pProperty-&gt;GetType();

         switch(propType) {
         case adBigInt:
            strMsg = "adBigInt";
            break;
         case adBinary:
            strMsg = "adBinary";
            break;
         case adBoolean:
            strMsg = "adBoolean";
            break;
         case adBSTR:
            strMsg = "adBSTR";
            break;
         case adChapter:
            strMsg = "adChapter";
            break;
         case adChar:
            strMsg = "adChar";
            break;
         case adCurrency:
            strMsg = "adCurrency";
            break;
         case adDate:
            strMsg = "adDate";
            break;
         case adDBDate:
            strMsg = "adDBDate";
            break;
         case adDBTime:
            strMsg = "adDBTime";
            break;
         case adDBTimeStamp:
            strMsg = "adDBTimeStamp";
            break;
         case adDecimal:
            strMsg = "adDecimal";
            break;
         case adDouble:
            strMsg = "adDouble";
            break;
         case adEmpty:
            strMsg = "adEmpty";
            break;
         case adError:
            strMsg = "adError";
            break;
         case adFileTime:
            strMsg = "adFileTime";
            break;
         case adGUID:
            strMsg = "adGUID";
            break;
         case adIDispatch:
            strMsg = "adIDispatch";
            break;
         case adInteger:
            strMsg = "adInteger";
            break;
         case adIUnknown:
            strMsg = "adIUnknown";
            break;
         case adLongVarBinary:
            strMsg = "adLongVarBinary";
            break;
         case adLongVarChar:
            strMsg = "adLongVarChar";
            break;
         case adLongVarWChar:
            strMsg = "adLongVarWChar";
            break;
         case adNumeric:
            strMsg = "adNumeric";
            break;
         case adPropVariant:
            strMsg = "adPropVariant";
            break;
         case adSingle:
            strMsg = "adSingle";
            break;
         case adSmallInt:
            strMsg = "adSmallInt";
            break;
         case adTinyInt:
            strMsg = "adTinyInt";
            break;
         case adUnsignedBigInt:
            strMsg = "adUnsignedBigInt";
            break;
         case adUnsignedInt:
            strMsg = "adUnsignedInt";
            break;
         case adUnsignedSmallInt:
            strMsg = "adUnsignedSmallInt";
            break;
         case adUnsignedTinyInt:
            strMsg = "adUnsignedTinyInt";
            break;
         case adUserDefined:
            strMsg = "adUserDefined";
            break;
         case adVarBinary:
            strMsg = "adVarBinary";
            break;
         case adVarChar:
            strMsg = "adVarChar";
            break;
         case adVariant:
            strMsg = "adVariant";
            break;
         case adVarNumeric:
            strMsg = "adVarNumeric";
            break;
         case adVarWChar:
            strMsg = "adVarWChar";
            break;
         case adWChar:
            strMsg = "adWChar";
            break;
         default:
            strMsg = "*UNKNOWN*";
            break;
         }

         intLineCnt++;

         printf ("Property %d : %s,Type = %s\n",iIndex, (LPCSTR)pProperty-&gt;GetName(),
            (LPCSTR)strMsg);
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      PrintComError(e);
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
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
<link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>