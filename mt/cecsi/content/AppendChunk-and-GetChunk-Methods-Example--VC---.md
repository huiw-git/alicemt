---
title: "AppendChunk and GetChunk Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51aa99be-d5ca-46ac-8b3f-1b03ce4f0b2a
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
# AppendChunk and GetChunk Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk</legacyLink> and <legacyLink xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk</legacyLink> methods to fill an image field with data from another record.</para>
    <code>// BeginAppendChunkCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#define ChunkSize 100

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include "conio.h"
#include "malloc.h"
#include "icrsint.h"

// extracts pubid, prinfo.
class CPubInfoRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CPubInfoRs)
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sz_pubid, sizeof(m_sz_pubid), l_pubid, TRUE)
   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_sz_prinfo, sizeof(m_sz_prinfo), l_prinfo, TRUE)
   END_ADO_BINDING()

public:
   CHAR m_sz_pubid[10];
   ULONG l_pubid;
   CHAR m_sz_prinfo[200];
   ULONG l_prinfo;    
};

//Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void AppendChunkX();
void PrintProviderError(_ConnectionPtr pConnection);

inline int myscanf(char* strDest, int n) {    
   char strExBuff[10];
   char* pstrRet = fgets(strDest, n, stdin);

   if (pstrRet == NULL)
      return 0;

   if (!strrchr(strDest, '\n'))
      // Exhaust the input buffer.
      do {
         fgets(strExBuff, sizeof(strExBuff), stdin);
      } while (!strrchr(strExBuff, '\n'));
   else
      // Replace '\n' with '\0'
      strDest[strrchr(strDest, '\n') - strDest] = '\0';

   return strlen(strDest);
}
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
   HRESULT  hr = S_OK;

   if (FAILED(::CoInitialize(NULL)))
      return -1;

   AppendChunkX();

   ::CoUninitialize();
}

void AppendChunkX() {
   // Define ADO object pointers, initialize pointers on define. These are in the ADODB::  namespace.
   _RecordsetPtr pRstPubInfo = NULL;
   _ConnectionPtr pConnection = NULL;
   char * token1;

   // Define other variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared.(VC++ Extensions)
   CPubInfoRs pubrs;   // C++ class object   

   HRESULT hr = S_OK;
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   _bstr_t strMessage,strPubID,strPRInfo;
   _variant_t varChunk;
   long lngOffSet,lngLogoSize;
   char pubId[50];
   lngOffSet = 0;

   UCHAR chData;
   SAFEARRAY FAR *psa;
   SAFEARRAYBOUND rgsabound[1];
   rgsabound[0].lLbound = 0;
   rgsabound[0].cElements = ChunkSize;

   try {
      // Open a Connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      hr = pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);

      TESTHR(hr= pRstPubInfo.CreateInstance(__uuidof(Recordset)));  

      pRstPubInfo-&gt;CursorType = adOpenKeyset;
      pRstPubInfo-&gt;LockType = adLockOptimistic;

      hr = pRstPubInfo-&gt;Open("pub_info", _variant_t((IDispatch*)pConnection,true),
                              adOpenKeyset, adLockOptimistic, adCmdTable);

      // Open an IADORecordBinding interface pointer for Binding Recordset to a class    
      TESTHR(pRstPubInfo-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here    
      TESTHR(picRs-&gt;BindToRecordset(&amp;pubrs));

      // Display the available logos here
      strMessage = "Available logos are: " + (_bstr_t)"\n\n";
      printf(strMessage);
      int Counter = 0;
      while (!(pRstPubInfo-&gt;EndOfFile)) { 
         printf("\n%s", pubrs.m_sz_pubid);
         printf("\n%s", strtok_s(pubrs.m_sz_prinfo, ",", &amp;token1));

         // Display 5 records at a time and wait for user to continue..
         if (++Counter &gt;= 5) {
            Counter = 0;
            printf("\nPress any key to continue...");
            _getch();
         }
         pRstPubInfo-&gt;MoveNext(); 
      }

      // Prompt For a Logo to Copy
      printf("\nEnter the ID of a logo to copy: ");
      myscanf(pubId, sizeof(pubId));
      strPubID = pubId;

      // Copy the logo to a variable in chunks
      pRstPubInfo-&gt;Filter = "pub_id = '"  + strPubID + "'";
      lngLogoSize = pRstPubInfo-&gt;Fields-&gt;Item["logo"]-&gt;ActualSize;

      // Create a safe array to store the array of BYTES  
      rgsabound[0].cElements = lngLogoSize;
      psa = SafeArrayCreate(VT_UI1, 1, rgsabound);

      long index1 = 0;
      while (lngOffSet &lt; lngLogoSize) {
         varChunk = pRstPubInfo-&gt;Fields-&gt;Item["logo"]-&gt;GetChunk(ChunkSize);

         // Copy the data only upto the Actual Size of Field.  
         for (long index = 0 ; index &lt;= (ChunkSize - 1) ; index++) {
            hr = SafeArrayGetElement(varChunk.parray, &amp;index, &amp;chData);
            if (SUCCEEDED(hr)) {
               // Take BYTE by BYTE and advance Memory Location
               hr = SafeArrayPutElement(psa, &amp;index1, &amp;chData); 
               index1++;
            }
            else
               break;
         }
         lngOffSet = lngOffSet + ChunkSize;
      }
      lngOffSet = 0;

      printf("Enter a new Pub Id: ");
      myscanf(pubrs.m_sz_pubid, sizeof(pubrs.m_sz_pubid));
      strPubID = pubrs.m_sz_pubid;
      printf("Enter descriptive text: " );
      mygets(pubrs.m_sz_prinfo, sizeof(pubrs.m_sz_prinfo));

      pRstPubInfo-&gt;AddNew();
      pRstPubInfo-&gt;Fields-&gt;GetItem("pub_id")-&gt;PutValue(strPubID);
      pRstPubInfo-&gt;Fields-&gt;GetItem("pr_info")-&gt;PutValue(pubrs.m_sz_prinfo);

      // Assign the Safe array  to a variant. 
      varChunk.vt = VT_ARRAY|VT_UI1;
      varChunk.parray = psa;
      hr = pRstPubInfo-&gt;Fields-&gt;GetItem("logo")-&gt;AppendChunk(varChunk); 

      // Update the table 
      pRstPubInfo-&gt;Update();

      lngLogoSize = pRstPubInfo-&gt;Fields-&gt;Item["logo"]-&gt;ActualSize;

      // Show the newly added record.
      printf("New Record : %s\n Description : %s\n Logo Size : %s",
         pubrs.m_sz_pubid,
         pubrs.m_sz_prinfo,(LPCSTR)(_bstr_t)pRstPubInfo-&gt;Fields-&gt;
         Item["logo"]-&gt;ActualSize);

      // Delete new record because this is demonstration.
      pConnection-&gt;Execute("DELETE FROM PUB_INFO WHERE pub_id = '"
         + strPubID +"'", NULL,adCmdText);
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      PrintProviderError(pConnection);
      printf("Source : %s \n Description : %s\n", (LPCSTR)bstrSource,
         (LPCSTR)bstrDescription);
   }

   // Clean up objects before exit.
   if (pRstPubInfo)
      if (pRstPubInfo-&gt;State == adStateOpen)
         pRstPubInfo-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
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
         printf("\t Error number: %x\t%s", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
      }
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk Method</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>