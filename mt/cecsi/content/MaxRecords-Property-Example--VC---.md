---
title: "MaxRecords Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af6b399b-e546-4de5-9cd1-5a6e0ec7ddc7
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
# MaxRecords Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords</legacyLink> property to open a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> containing the 10 most expensive titles in the <legacyBold><legacyItalic>Titles</legacyItalic></legacyBold> table.</para>
  </introduction>
  <codeExample>
    <code>// MaxRecords_Property_Example.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF","EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// This class extracts titles and type from the titles table
class CTitleRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CTitleRs)

      // Column title is the 1st field in the Recordset
      ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar,m_szau_Title,
      sizeof(m_szau_Title), lau_TitleStatus, FALSE)

      // Column price is the 2nd field in the Recordset
      ADO_VARIABLE_LENGTH_ENTRY2(2, adDouble, m_szau_Price,
      sizeof(m_szau_Price), lau_PriceStatus, FALSE)

   END_ADO_BINDING()

public:
   CHAR m_szau_Title[81];
   ULONG lau_TitleStatus;
   DOUBLE m_szau_Price;
   ULONG lau_PriceStatus;
};

// Function Declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void MaxRecordsX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   MaxRecordsX();
   ::CoUninitialize();
}

void  MaxRecordsX() {
   // Define ADO ObjectPointers.  Initialize Pointers on define
   // These are in the ADODB :: namespace
   _RecordsetPtr pRstTemp = NULL;

   // Define Other Variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer Declared  
   CTitleRs titlers;   // C++ Class Object

   try {
      // Assign Connection String to Variable
      _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

      // Open Recordset containing the 10 most expensive titles in the Titles table.
      TESTHR(pRstTemp.CreateInstance(__uuidof(Recordset)));

      pRstTemp-&gt;MaxRecords = 10;

      pRstTemp-&gt;Open("SELECT title,price FROM Titles ORDER BY Price DESC",
         strCnn, adOpenForwardOnly, adLockReadOnly, adCmdText);

      // Open IADORecordBinding interface pointer for binding Recordset to a class
      TESTHR(pRstTemp-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ class here
      TESTHR(picRs-&gt;BindToRecordset(&amp;titlers));

      // Display the contents of the Recordset
      printf("Top Ten Titles by Price:\n\n");

      while ( !(pRstTemp-&gt;EndOfFile) ) {
         printf("%s ---  %6.2lf\n", titlers.lau_TitleStatus == adFldOK ? 
            titlers.m_szau_Title : "&lt;NULL&gt;", titlers.lau_PriceStatus == adFldOK ? 
            titlers.m_szau_Price : 0.00);
         pRstTemp-&gt;MoveNext();
      }
   }
   catch(_com_error &amp;e) {
      // Display errors, if any.  Pass connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstTemp-&gt;GetActiveConnection();

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

   // Clean up objects before exit. Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

   if (pRstTemp)
      if (pRstTemp-&gt;State == adStateOpen)
         pRstTemp-&gt;Close();
};

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object
   // pErr is a record object in the Connection's Error collection
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count)&gt;0 ) {
      long nCount = pConnection-&gt;Errors-&gt;Count;

      // Collection ranges from 0 to nCount-1
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error Number :%x \t %s", pErr-&gt;Number, pErr-&gt;Description);
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
        <computerOutput>Top Ten Titles by Price:

But Is It User Friendly? ---   22.95
Computer Phobic AND Non-Phobic Individuals: Behavior Variations ---   21.59
Onions, Leeks, and Garlic: Cooking Secrets of the Mediterranean ---   20.95
Secrets of Silicon Valley ---   20.00
The Busy Executive's Database Guide ---   19.99
Straight Talk About Computers ---   19.99
Silicon Valley Gastronomic Treats ---   19.99
Prolonged Data Deprivation: Four Case Studies ---   19.99
Sushi, Anyone? ---   14.99
Fifty Years in Buckingham Palace Kitchens ---   11.95</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>