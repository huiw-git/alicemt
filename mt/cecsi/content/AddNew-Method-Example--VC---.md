---
title: "AddNew Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9cc8774b-6711-4837-b442-959eaf79343e
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
# AddNew Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method to create a new record with the specified name.</para>
    <code>// BeginAddNewCpp.cpp
// compile with: /EHsc /c
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include "conio.h"
#include "icrsint.h"

// class extracts empid, fname and lastname
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)

   // Column empid is the 1st field in the recordset   
   ADO_VARIABLE_LENGTH_ENTRY2(1, adVarChar, m_sz_empid, sizeof(m_sz_empid), 
                              lemp_empidStatus, TRUE)

   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_sz_fname, sizeof(m_sz_fname), 
                              lemp_fnameStatus, TRUE)

   ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_sz_lname, sizeof(m_sz_lname), 
                              lemp_lnameStatus, TRUE)

   END_ADO_BINDING()

public:
   CHAR m_sz_empid[10];
   ULONG lemp_empidStatus;
   CHAR m_sz_fname[40];
   ULONG lemp_fnameStatus;
   CHAR m_sz_lname[41];
   ULONG lemp_lnameStatus;
};

// Function declaration
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void AddNewX();
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

int main() {
   HRESULT hr = S_OK;
   if (FAILED(::CoInitialize(NULL))) 
      return -1;

   if (SUCCEEDED(hr)) {
      AddNewX();
      ::CoUninitialize();
   }
}

void AddNewX() {
   // Define ADO object pointers. Initialize pointers on define.
   _RecordsetPtr pRstEmployees = NULL;
   _ConnectionPtr pConnection = NULL;

   // Define Other variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared.(VC++ Extensions)   
   CEmployeeRs emprs;   // C++ class object   

   HRESULT hr = S_OK;

   // Replace Data Source value with your server name.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");
   _bstr_t strId;
   _bstr_t strMessage;

   try {
      // Open a connection
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);

      // Open employee table 
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));

      // You have to explicitly pass the Cursor type and LockType to the Recordset here
      pRstEmployees-&gt;Open("employee", _variant_t((IDispatch *) pConnection, true),
                          adOpenKeyset, adLockOptimistic, adCmdTable);

      // Open IADORecordBinding interface pointer for Binding Recordset to a class    
      TESTHR(pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ Class here   
      TESTHR(picRs-&gt;BindToRecordset(&amp;emprs));         

      // Get data from the user.The employee id must be formatted as first,middle and last 
      // initial, five numbers,then M or F to signify the gender. For example, the 
      // employee id for Bill A. Sorensen would be "BAS55555M". 
      printf("Enter Employee Id: ");
      myscanf(emprs.m_sz_empid, sizeof(emprs.m_sz_empid));
      strId = emprs.m_sz_empid;
      printf("Enter First Name: ");
      myscanf(emprs.m_sz_fname, sizeof(emprs.m_sz_fname));
      printf("Enter Last Name:");
      myscanf(emprs.m_sz_lname, sizeof(emprs.m_sz_lname));

      // Proceed if user entered id, the first and the last name. 

      if (strcmp(emprs.m_sz_empid, "") &amp;&amp; strcmp(emprs.m_sz_fname, "") &amp;&amp; strcmp(emprs.m_sz_lname, "")) {
         // This adds a new record to the table   
         // if (FAILED(hr = picRs-&gt;AddNew(&amp;emprs)))
         //_com_issue_error(hr);
         TESTHR(picRs-&gt;AddNew(&amp;emprs));

         // Show the newly added data
         printf("New Record: %s  %s  %s \n",\
            emprs.lemp_empidStatus == adFldOK ? emprs.m_sz_empid : "&lt;NULL&gt;",\
            emprs.lemp_fnameStatus == adFldOK ? emprs.m_sz_fname : "&lt;NULL&gt;",\
            emprs.lemp_lnameStatus == adFldOK ? emprs.m_sz_lname : "&lt;NULL&gt;");
      }
      else
         printf("Please enter an employee id, first name and last name.\n");    

      // Delete the new record because this is a demonstration. 
      pConnection-&gt;Execute("DELETE FROM EMPLOYEE WHERE emp_id = '" + strId + "'", NULL, adCmdText);
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _variant_t vtConnect = pRstEmployees-&gt;GetActiveConnection();

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

   // Clean up objects before exit.  Release the IADORecordset Interface here   
   if (picRs)
      picRs-&gt;Release();

   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
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
         printf("\n\t Error number: %x\t%s", pErr-&gt;Number, (LPCSTR)pErr-&gt;Description);
      }
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>