---
title: "Clone Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36b96e3d-8cb0-4b79-bd93-ea5e0eb5679f
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
# Clone Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink> method to create copies of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and then lets the user position the record pointer of each copy independently.</para>
    <para>Use the following example in an Active Server Page (ASP). This example uses the <legacyBold>Northwind</legacyBold> database distributed with Microsoft Access. Cut and paste the following code to Notepad or another text editor and save it as CloneVBS.asp. You can view the result in any client browser.</para>
    <para>To exercise the example, change the line <codeInline>RsCustomerList.Source = "Customers"</codeInline> to <codeInline>RsCustomerList.Source = "Products"</codeInline> to count a larger table.</para>
    <code>&lt;!-- BeginCloneVBS --&gt;
&lt;% Language = VBScript %&gt;
&lt;%' use this meta tag instead of adovbs.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;TITLE&gt;ADO Clone Method&lt;/TITLE&gt;
&lt;/HEAD&gt;

&lt;BODY&gt;

&lt;H1 align="center"&gt;ADO Clone Method&lt;/H1&gt;
&lt;HR&gt;
&lt;% ' to integrate/test this code replace the 
   ' Data Source value in the Connection string%&gt;
&lt;% 
    ' connection and recordset variables
    Dim Cnxn, strCnxn
    Dim rsCustomers, strSQLCustomers
    Dim rsFirst, rsLast, rsCount
    Dim rsClone
    Dim CloneFirst, CloneLast, CloneCount

    ' open connection
    Set Cnxn = Server.CreateObject("ADODB.Connection")
    strCnxn = "Provider='sqloledb';Data Source=" &amp; _
            Request.ServerVariables("SERVER_NAME") &amp; ";" &amp; _
            "Integrated Security='SSPI';Initial Catalog='Northwind';"
    Cnxn.Open strCnxn
        
    ' create and open Recordset using object refs
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")
    strSQLCustomers = "Customers"
    
    rsCustomers.ActiveConnection = Cnxn
    rsCustomers.CursorLocation = adUseClient
    rsCustomers.CursorType = adOpenKeyset
    rsCustomers.LockType = adLockOptimistic
    rsCustomers.Source = strSQLCustomers
    rsCustomers.Open

    rsCustomers.MoveFirst
    rsCount = rsCustomers.RecordCount
    rsFirst = rsCustomers("CompanyName")
    rsCustomers.MoveLast
    rsLast = rsCustomers("CompanyName")

    ' create clone
    Set rsClone = rsCustomers.Clone
    rsClone.MoveFirst
    CloneCount = rsClone.RecordCount
    CloneFirst = rsClone("CompanyName")
    rsClone.MoveLast
    CloneLast = rsClone("CompanyName")
%&gt;

&lt;!-- Display Results --&gt;
&lt;H3&gt;There Are &lt;%=rsCount%&gt; Records in the original recordset&lt;/H3&gt;
&lt;H3&gt;The first record is &lt;%=rsFirst%&gt; and the last record is &lt;%=rsLast%&gt;&lt;/H3&gt;
&lt;BR&gt;&lt;HR&gt;
&lt;H3&gt;There Are &lt;%=CloneCount%&gt; Records in the original recordset&lt;/H3&gt;
&lt;H3&gt;The first record is &lt;%=CloneFirst%&gt; and the last record is &lt;%=CloneLast%&gt;&lt;/H3&gt;
&lt;BR&gt;&lt;HR&gt;
&lt;H4&gt;Location of OLEDB Database&lt;/H4&gt;

&lt;%
    ' Show location of DSN data source
    Response.Write(Cnxn)

    ' Clean up
    If rsCustomers.State = adStateOpen then
       rsCustomers.Close
    End If
    If rsClone.State = adStateOpen then
       rsClone.Close
    End If
    If Cnxn.State = adStateOpen then
       Cnxn.Close
    End If
    Set rsCustomers = Nothing
    Set rsClone = Nothing
    Set Cnxn = Nothing
%&gt;
&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndCloneVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>