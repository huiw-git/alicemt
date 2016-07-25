---
title: "Seek Method and Index Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57bda520-e98b-443c-a8bc-d8430e89a383
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
# Seek Method and Index Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink> method and <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink> property in conjunction with a given <legacyBold><legacyItalic>Employee ID</legacyItalic></legacyBold>, to locate the employee's name in the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table of the Nwind.mdb database.</para>
    <code>// BeginSeekCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;conio.h&gt;
#include &lt;string.h&gt;
#include "icrsint.h"

// Class extracts only EmployeeId,FirstName and LastName from employees table
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)

   // Column hiredate is the 1st field in the table.
   ADO_VARIABLE_LENGTH_ENTRY2(1, adInteger,m_ie_empid, sizeof(m_ie_empid), 
                              le_empidStatus, FALSE)

   // Column LastName is the 2nd field in the table.
   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sze_lname, sizeof(m_sze_lname), 
                             le_lnameStatus, FALSE)

   // Column FirstName is the 3rd field in the table.
   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sze_fname, sizeof(m_sze_fname), 
                             le_fnameStatus, FALSE)
   END_ADO_BINDING()

public:
   INT m_ie_empid;
   ULONG le_empidStatus;
   CHAR m_sze_fname[11];
   ULONG le_fnameStatus;
   CHAR m_sze_lname[21];
   ULONG le_lnameStatus;    
};

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void SeekX();
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
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   SeekX();
   ::CoUninitialize();
}

void SeekX() {
   HRESULT hr = S_OK;

   // Define ADO object pointers, initialize pointers on define. These are in the ADODB::  namespace.
   _RecordsetPtr pRstEmp = NULL;

   IADORecordBinding *picRs = NULL;   // Interface Pointer declared
   CEmployeeRs EmpRs;   // C++ class object

   // Definitions of other variables
   _bstr_t strPrompt("Enter an EmployeeID (e.g., 1 to 9)");
   char strEmpId[2];

   try {
      TESTHR(pRstEmp.CreateInstance(__uuidof(Recordset)));
      pRstEmp-&gt;CursorLocation = adUseServer;
      pRstEmp-&gt;Open("employees", "Provider='Microsoft.Jet.OLEDB.4.0';" 
         "Data Source='C:\\Program Files\\Microsoft Office\\Office\\"
         "Samples\\Northwind.mdb';",
         adOpenKeyset,adLockReadOnly,adCmdTableDirect);

      // Open an IADORecordBinding interface pointer which 
      // we'll use for binding Recordset to a Class  
      TESTHR(pRstEmp-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class
      TESTHR(picRs-&gt;BindToRecordset(&amp;EmpRs));

      // Does this provider support Seek and Index?
      if (pRstEmp-&gt;Supports(adIndex) &amp;&amp; pRstEmp-&gt;Supports(adSeek)) {
         pRstEmp-&gt;Index = "PrimaryKey";

         // Display all the employees.
         pRstEmp-&gt;MoveFirst();
         while (!pRstEmp-&gt;EndOfFile) {
            printf("%d : %s %s\n",  
               EmpRs.le_empidStatus == adFldOK ? 
               EmpRs.m_ie_empid : 0, 
               EmpRs.le_fnameStatus == adFldOK ? 
               EmpRs.m_sze_fname : "&lt;NULL&gt;", 
               EmpRs.le_lnameStatus == adFldOK ? 
               EmpRs.m_sze_lname : "&lt;NULL&gt;");

            pRstEmp-&gt;MoveNext();
         }
         // Prompt the user for an EmployeeID between 1 and 9.
         do {
            pRstEmp-&gt;MoveFirst();
            printf("\n\n%s\t",(LPCSTR) strPrompt);
            mygets(strEmpId, 2);

            // Quit if strEmpID is a zero-length string (CANCEL, null, etc.)
            char *strTemp = strtok_s(strEmpId," \t", NULL);
            if (strTemp == NULL) break;
            if (strlen(strTemp) == 1 &amp;&amp; atoi(strTemp) &gt;= 1 &amp;&amp; atoi(strTemp) &lt;= 9) {
               _variant_t strEmployeeId(strTemp);
               pRstEmp-&gt;Seek(strEmployeeId, adSeekAfterEQ);
               if (pRstEmp-&gt;EndOfFile)
                  printf("Employee not found.\n");
               else {
                  printf("%d : Employee='%s %s'\n",  
                     EmpRs.le_empidStatus == adFldOK ? 
                     EmpRs.m_ie_empid : 0,
                     EmpRs.le_fnameStatus == adFldOK ? 
                     EmpRs.m_sze_fname : "&lt;NULL&gt;", 
                     EmpRs.le_lnameStatus == adFldOK ? 
                     EmpRs.m_sze_lname : "&lt;NULL&gt;");
               }
            }
         } while(true);
      }  
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstEmp-&gt;GetActiveConnection();

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

   // Clean up objects before exit.  Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

   if (pRstEmp)
      if (pRstEmp-&gt;State == adStateOpen)
         pRstEmp-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
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

   // Print COM errors. 
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s\n", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>