---
title: "Handling Errors in VBScript"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31bc3743-32d3-4bc7-ac61-ee6ed0fdec70
caps.latest.revision: 3
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
# Handling Errors in VBScript
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>There is little difference between the methods used in Visual Basic and those used with VBScript. The primary difference is that VBScript does not support the concept of error handling by continuing execution at a label. In other words, you cannot use <codeInline>On Error GoTo</codeInline> in VBScript. Instead, use <codeInline>On Error Resume Next</codeInline> and then check both <legacyBold>Err.Number</legacyBold> and the <legacyBold>Count</legacyBold> property of the <legacyBold>Errors</legacyBold> collection, as shown in the following example:</para>
  </introduction>
  <section>
    <content>
      <code>&lt;!-- BeginErrorExampleVBS --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;TITLE&gt;Error Handling Example (VBScript)&lt;/TITLE&gt;
&lt;/HEAD&gt;
&lt;BODY&gt;

&lt;h1&gt;Error Handling Example (VBScript)&lt;/h1&gt;

&lt;%

   Dim cnn1
   Dim errLoop
   Dim strError

   On Error Resume Next
      
   ' Intentionally trigger an error.
   Set cnn1 = Server.CreateObject("ADODB.Connection")
   cnn1.Open "nothing"

   If cnn1.Errors.Count &gt; 0 Then
      ' Enumerate Errors collection and display
      ' properties of each Error object.
      For Each errLoop In cnn1.Errors
         strError = "Error #" &amp; errLoop.Number &amp; "&lt;br&gt;" &amp; _
            "   " &amp; errLoop.Description &amp; "&lt;br&gt;" &amp; _
            "   (Source: " &amp; errLoop.Source &amp; ")" &amp; "&lt;br&gt;" &amp; _
            "   (SQL State: " &amp; errLoop.SQLState &amp; ")" &amp; "&lt;br&gt;" &amp; _
            "   (NativeError: " &amp; errLoop.NativeError &amp; ")" &amp; "&lt;br&gt;"
         If errLoop.HelpFile = "" Then
            strError = strError &amp; _
               "   No Help file available" &amp; _
               "&lt;br&gt;&lt;br&gt;"
         Else
            strError = strError &amp; _
               "   (HelpFile: " &amp; errLoop.HelpFile &amp; ")" &amp; "&lt;br&gt;" &amp; _
               "   (HelpContext: " &amp; errLoop.HelpContext &amp; ")" &amp; _
               "&lt;br&gt;&lt;br&gt;"
         End If
                  

         Response.Write("&lt;p&gt;" &amp; strError &amp; "&lt;/p&gt;")
      Next
   End If

%&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndErrorExampleVBS --&gt;</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>