---
title: "ADO Errors"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bb84114-a1df-4122-a1b8-ad98dcd85cc3
caps.latest.revision: 7
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
# ADO Errors
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO errors are reported to your program as run-time errors. You can use the error-trapping mechanism of your programming language to trap and handle them. For example, in Visual Basic, use the <legacyBold>On Error</legacyBold> statement. In Visual J++, use a <legacyBold>try-catch</legacyBold> block. In Visual C++, it depends on the method you are using to access the ADO libraries. With #import, use a <legacyBold>try-catch</legacyBold> block. Otherwise, C++ programmers need to explicitly retrieve the error object by calling <legacyBold>GetErrorInfo</legacyBold>. The following Visual Basic sub procedure demonstrates trapping an ADO error:</para>
    <code>' BeginErrorHandlingVB01
Private Sub Form_Load()
' Turn on error handling
On Error GoTo FormLoadError

'Open the database and the recordset for processing.
'
Dim strCnn As String
strCnn = "Provider=sqloledb;" &amp; _
    "Data Source=a-iresmi2000;" &amp; _
    "Initial Catalog=Northwind;Integrated Security=SSPI"

' cnn is a Public Connection Object because
' it was defined WithEvents
Set cnn = New ADODB.Connection
cnn.Open strCnn

' The next line of code intentionally causes
' an error by trying to open a connection
' that has already been opened.
cnn.Open strCnn

' rst is a Public Recordset because it
' was defined WithEvents
Set rst = New ADODB.Recordset
rst.Open "Customers", cnn

Exit Sub

' Error handler
FormLoadError:
    Dim strErr As String
    Select Case Err
        Case adErrObjectOpen
            strErr = "Error #" &amp; Err.Number &amp; ": " &amp; Err.Description &amp; vbCrLf
            strErr = strErr &amp; "Error reported by: " &amp; Err.Source &amp; vbCrLf
            strErr = strErr &amp; "Help File: " &amp; Err.HelpFile &amp; vbCrLf
            strErr = strErr &amp; "Topic ID: " &amp; Err.HelpContext
            MsgBox strErr
            Debug.Print strErr
            Err.Clear
            Resume Next
        ' If some other error occurs that
        ' has nothing to do with ADO, show
        ' the number and description and exit.
        Case Else
            strErr = "Error #" &amp; Err.Number &amp; ": " &amp; Err.Description &amp; vbCrLf
            MsgBox strErr
            Debug.Print strErr
            Unload Me
    End Select
End Sub
' EndErrorHandlingVB01</code>
    <para>This <legacyBold>Form_Load</legacyBold> event procedure intentionally creates an error by trying to open the same <legacyBold>Connection</legacyBold> object twice. The second time the <legacyBold>Open</legacyBold> method is called, the error handler is activated. In this case the error is of type <legacyBold>adErrObjectOpen</legacyBold>, so the error handler displays the following message before resuming program execution:</para>
    <code>Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705</code>
    <para>The error message includes each piece of information provided by the Visual Basic <legacyBold>Err</legacyBold> object except for the <legacyBold>LastDLLError</legacyBold> value, which does not apply here. The error number tells you which error has occurred. The description is useful in cases in which you do not want to handle the error yourself. You can simply pass it along to the user. Although you will usually want to use messages customized for your application, you cannot anticipate every error; the description gives some clue as to what went wrong. In the sample code, the error was reported by the <legacyBold>Connection</legacyBold> object. You will see the object's type or programmatic ID here — not a variable name.</para>
    <alert class="note">
      <para>The Visual Basic <legacyBold>Err</legacyBold> object only contains information about the most recent error. The ADO <legacyBold>Errors</legacyBold> collection of the <legacyBold>Connection </legacyBold>object contains one <legacyBold>Error</legacyBold> object for each error raised by the most recent ADO operation. Use the <legacyBold>Errors</legacyBold> collection rather than the <legacyBold>Err </legacyBold>object to handle multiple errors. For more information about the <legacyBold>Errors</legacyBold> collection, see <legacyLink xlink:href="cc7d6ff9-2034-45c6-9d61-90b177010054">Provider Errors</legacyLink>. However, if there is no valid <legacyBold>Connection</legacyBold> object, the <legacyBold>Err</legacyBold> object is the only source for information about ADO errors.</para>
    </alert>
    <para>What kinds of operations are likely to cause ADO errors? Common ADO errors can involve opening an object such as a <legacyBold>Connection</legacyBold> or <legacyBold>Recordset</legacyBold>, attempting to update data, or calling a method or property that is not supported by your provider.</para>
    <para>OLE DB errors can also be passed to your application as run-time errors in the <legacyBold>Errors</legacyBold> collection.</para>
    <para>The following topic provides more information about ADO errors.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="f653393e-d4b0-4c34-ad5f-2bdf56bc1305">ADO Error Reference</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>