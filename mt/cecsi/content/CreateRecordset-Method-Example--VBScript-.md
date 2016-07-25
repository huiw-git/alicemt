---
title: "CreateRecordset Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cce0d8b5-e87b-4f7b-a8a0-37d5025a1f5d
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
# CreateRecordset Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This code example creates a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> on the server side. It has two columns with four rows each. Cut and paste the following code to Notepad or another text editor and save it as <legacyBold>CreateRecordsetVBS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginCreateRecordsetVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;CreateRecordset Method Example (VBScript)&lt;/title&gt;
&lt;style&gt;
&lt;!--
body {
   font-family: 'Verdana','Arial','Helvetica',sans-serif;
   BACKGROUND-COLOR:white;
   COLOR:black;
    }
.thead {
   background-color: #008080; 
   font-family: 'Verdana','Arial','Helvetica',sans-serif; 
   font-size: x-small;
   color: white;
   }
.thead2 {
   background-color: #800000; 
   font-family: 'Verdana','Arial','Helvetica',sans-serif; 
   font-size: x-small;
   color: white;
   }
.tbody { 
   text-align: center;
   background-color: #f7efde;
   font-family: 'Verdana','Arial','Helvetica',sans-serif; 
   font-size: x-small;
    }
--&gt;
&lt;/style&gt;
&lt;/head&gt;

&lt;body&gt;

&lt;OBJECT classid=clsid:BD96C556-65A3-11D0-983A-00C04FC29E33 height=1 id=DC1 width=1&gt;
&lt;/OBJECT&gt;
&lt;h1&gt;CreateRecordset Method Example (VBScript)&lt;/h1&gt;
&lt;script language = "vbscript"&gt;
    ' use the RDS.DataControl to create an empty recordset; 
    ' takes an array of variants where every element is itself another
    ' array of variants, one for every column required in the recordset
   
    ' the elements of the inner array are the column's
    ' name, type, size, and nullability
Sub GetRS()
   Dim Record(2)
   Dim Field1(3)
   Dim Field2(3)
   Dim Field3(3)

    ' for each field, specify the name type, size, and nullability

   Field1(0) = "Name"   ' Column name.
   Field1(1) = CInt(129)   ' Column type.
   Field1(2) = CInt(40)   ' Column size.
   Field1(3) = False      ' Nullable?

   Field2(0) = "Age"
   Field2 (1) = CInt(3)
   Field2 (2) = CInt(-1)
   Field2 (3) = True

   Field3 (0) = "DateOfBirth"
   Field3 (1) = CInt(7)
   Field3 (2) = CInt(-1)
   Field3 (3) = True

    ' put all fields into an array of arrays
   Record(0) = Field1
   Record(1) = Field2
   Record(2) = Field3

   Dim NewRs 
   Set NewRS = DC1.CreateRecordset(Record)

   Dim fields(2)
   fields(0) = Field1(0)
   fields(1) = Field2(0)
   fields(2) = Field3(0)

    ' Populate the new recordset with data values.
   Dim fieldVals(2)

    ' Use AddNew to add the records.
   fieldVals(0) = "Joe"
   fieldVals(1) = 5
   fieldVals(2) = CDate(#1/5/96#)
   NewRS.AddNew fields, fieldVals

   fieldVals(0) = "Mary"
   fieldVals(1) = 6
   fieldVals(2) = CDate(#6/5/94#)
   NewRS.AddNew fields, fieldVals

   fieldVals(0) = "Alex"
   fieldVals(1) = 13
   fieldVals(2) = CDate(#1/6/88#)
   NewRS.AddNew fields, fieldVals

   fieldVals(0) = "Susan"
   fieldVals(1) = 13
   fieldVals(2) = CDate(#8/6/87#)
   NewRS.AddNew fields, fieldVals
   
   NewRS.MoveFirst

    ' Set the newly created and populated Recordset to
    ' the SourceRecordset property of the
    ' RDS.DataControl to bind to visual controls

   Set DC1.SourceRecordset = NewRS
End Sub
&lt;/script&gt;
&lt;table datasrc="#DC1" align="center"&gt;
&lt;thead&gt;
&lt;tr id="ColHeaders" class="thead2"&gt;
   &lt;th&gt;Name&lt;/th&gt;
   &lt;th&gt;Age&lt;/th&gt;
    &lt;th&gt;D.O.B.&lt;/th&gt;
&lt;/tr&gt;
&lt;/thead&gt;
&lt;tbody class="tbody"&gt;
&lt;tr&gt;
   &lt;td&gt;&lt;input datafld="Name" size=15 id=text1 name=text1&gt; &lt;/td&gt;
   &lt;td&gt;&lt;input datafld="Age" size=25 id=text2 name=text2&gt; &lt;/td&gt;
   &lt;td&gt;&lt;input datafld="DateOfBirth" size=25 id=text3 name=text3&gt; &lt;/td&gt;
&lt;/tr&gt;
&lt;/tbody&gt;
&lt;/table&gt;
&lt;input type = "button" onclick = "GetRS()" value="Go!"&gt;
&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndCreateRecordsetVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset Method (RDS)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>