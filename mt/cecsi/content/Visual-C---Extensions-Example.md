---
title: "Visual C++ Extensions Example"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9739c278-582c-402b-a158-7f68a1b2c293
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
# Visual C++ Extensions Example
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This program shows how values are retrieved from fields and converted to C/C++ variables.</para>
    <para>This example also takes advantage of "smart pointers," which automatically handle the COM-specific details of calling <codeInline>QueryInterface</codeInline> and reference counting for the <legacyBold>IADORecordBinding</legacyBold> interface.</para>
    <para>Without smart pointers, you would code:</para>
    <code>IADORecordBinding   *picRs = NULL;
...
TESTHR(pRs-&gt;QueryInterface(
          __uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));
...
if (picRs) picRs-&gt;Release();</code>
    <para>With smart pointers, you derive the <codeInline>IADORecordBindingPtr</codeInline> type from the <codeInline>IADORecordBinding</codeInline> interface with this statement:</para>
    <code>_COM_SMARTPTR_TYPEDEF(IADORecordBinding, __uuidof(IADORecordBinding));</code>
    <para>And instantiate the pointer like this:</para>
    <code>IADORecordBindingPtr picRs(pRs);</code>
    <para>Because the Visual C++ Extensions are implemented by the <legacyBold>Recordset</legacyBold> object, the constructor for the smart pointer, <codeInline>picRs</codeInline>, takes the _<codeInline>RecordsetPtr</codeInline> pointer, <codeInline>pRs</codeInline>. The constructor calls <codeInline>QueryInterface</codeInline> using <codeInline>pRs</codeInline> to find the <codeInline>IADORecordBinding</codeInline> interface.</para>
    <code>// Visual_Cpp_Extensions_Example.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;icrsint.h&gt;
_COM_SMARTPTR_TYPEDEF(IADORecordBinding, __uuidof(IADORecordBinding));

inline void TESTHR(HRESULT _hr) { if FAILED(_hr) _com_issue_error(_hr); }

class CCustomRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CCustomRs)
      ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_ch_fname, sizeof(m_ch_fname), m_ul_fnameStatus, false)
      ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_ch_lname, sizeof(m_ch_lname), m_ul_lnameStatus, false)
   END_ADO_BINDING()

public:
   CHAR m_ch_fname[22];
   CHAR m_ch_lname[32];
   ULONG m_ul_fnameStatus;
   ULONG m_ul_lnameStatus;
};

int main() {
   ::CoInitialize(NULL);
   try {
      _RecordsetPtr pRs("ADODB.Recordset");
      CCustomRs rs;
      IADORecordBindingPtr picRs(pRs);

      pRs-&gt;Open(L"SELECT * FROM Employee ORDER BY lname", L"dsn=DataPubs;Trusted_Connection=yes;", adOpenStatic, adLockOptimistic, adCmdText);

      TESTHR(picRs-&gt;BindToRecordset(&amp;rs));

      while (!pRs-&gt;EndOfFile) {
         // Process data in the CCustomRs C++ instance variables.
         printf("Name = %s %s\n",
            (rs.m_ul_fnameStatus == adFldOK ? rs.m_ch_fname: "&lt;Error&gt;"), 
            (rs.m_ul_lnameStatus == adFldOK ? rs.m_ch_lname: "&lt;Error&gt;") );

         // Move to the next row of the Recordset.   Fields in the new row will 
         // automatically be placed in the CCustomRs C++ instance variables.

         pRs-&gt;MoveNext();
      }
   }
   catch (_com_error &amp;e ) {
      printf("Error:\n");
      printf("Code = %08lx\n", e.Error());
      printf("Meaning = %s\n", e.ErrorMessage());
      printf("Source = %s\n", (LPCSTR) e.Source());
      printf("Description = %s\n", (LPCSTR) e.Description());
   }
   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ff759185-df41-4507-8d12-0921894ffbd9">Using Visual C++ Extensions for ADO</link>
<link xlink:href="e492d307-24cb-489c-a5b0-99cdc09b07da">Visual C++ Extensions Header</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>