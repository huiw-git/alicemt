---
title: "ADO Event Instantiation: Visual Basic"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
caps.latest.revision: 8
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
# ADO Event Instantiation: Visual Basic
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In order to handle ADO events in Microsoft® Visual Basic®, you must declare a module-level variable using the <legacyBold>WithEvents</legacyBold> keyword. The variable can be declared only as part of a class module and must be declared at the module level. This is not as restrictive as it seems, however, because Visual Basic <legacyBold>Form</legacyBold> objects are also classes. The simplest way to handle ADO events is to declare a variable using <legacyBold>WithEvents</legacyBold>. The following example handles the <legacyBold>ConnectComplete</legacyBold> event for a <legacyBold>Connection</legacyBold> object:</para>
  </introduction>
  <section>
    <content>
      <code>' BeginEventExampleVB02
Dim WithEvents connEvent As Connection
Attribute connEvent.VB_VarHelpID = -1

Private Sub Form_Load()
Dim strConn As String

   ' Create a new object with event
   ' handling enabled.
   strConn = "Provider=sqloledb;" &amp; _
      "Data Source=MyServer;" &amp; _
      "Initial Catalog=Northwind;" &amp; _
      "Integrated Security=SSPI;"
   Set connEvent = New ADODB.Connection
   connEvent.Open strConn
End Sub

Private Sub connEvent_ConnectComplete(ByVal pError As ADODB.Error, _
    adStatus As ADODB.EventStatusEnum, _
    ByVal pConnection As ADODB.Connection)
Dim strMsg As String

   If adStatus = adStatusErrorsOccurred Then
      Select Case pError.Number
         Case adErrOperationCancelled
            ' The operation was cancelled in the
            ' Will event. Notify the user and exit.
            strMsg = "I'm sorry you can't connect right now." &amp; vbCrLf
            strMsg = strMsg &amp; "Click OK to exit."
            Unload Me
         Case Else
            strMsg = "Error " &amp; Format(pError.Number) &amp; vbCrLf
            strMsg = strMsg &amp; pError.Description
            strMsg = strMsg &amp; "Click OK to exit."
            Unload Me
      End Select
   End If
   frmWait.btnOK.Enabled = True
End Sub
' EndEventExampleVB02</code>
      <para>The <legacyBold>Connection</legacyBold> object is declared at the <legacyBold>Form</legacyBold> level using the <legacyBold>WithEvents</legacyBold> keyword to enable event handling. The Form_Load event handler actually creates the object by assigning a new <legacyBold>Connection</legacyBold> object to <legacyItalic>connEvent</legacyItalic> and then opens the connection. Of course, a real application would do more processing in the Form_Load event handler than is shown here.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>