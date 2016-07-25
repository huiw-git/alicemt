---
title: "Provider Errors"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc7d6ff9-2034-45c6-9d61-90b177010054
caps.latest.revision: 4
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
# Provider Errors
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When a provider error occurs, a run-time error of -2147467259 is returned. When you receive this error, check the <legacyBold>Errors</legacyBold> collection of the active <legacyBold>Connection</legacyBold> object, which will contain one or more errors describing what occurred.</para>
  </introduction>
  <section>
    <title>The ADO Errors Collection</title>
    <content>
      <para>Because a particular ADO operation can produce multiple provider errors, ADO exposes a collection of error objects through the <legacyBold>Connection</legacyBold> object. This collection contains no objects if an operation concludes successfully and contains one or more <legacyBold>Error</legacyBold> objects if something went wrong and the provider raised one or more errors. Examine each error object to determine the exact cause of the error.</para>
      <para>As soon as you have finished handling any errors that have occurred, you can clear the collection by calling the <legacyBold>Clear</legacyBold> method. It is especially important to explicitly clear the <legacyBold>Errors</legacyBold> collection before you call the <legacyBold>Resync</legacyBold>, <legacyBold>UpdateBatch</legacyBold>, or <legacyBold>CancelBatch</legacyBold> method on a <legacyBold>Recordset</legacyBold> object, the <legacyBold>Open</legacyBold> method on a <legacyBold>Connection</legacyBold> object, or set the <legacyBold>Filter</legacyBold> property on a <legacyBold>Recordset</legacyBold> object. By clearing the collection explicitly, you can be certain that any <legacyBold>Error</legacyBold> objects in the collection are not left over from a previous operation.</para>
      <para>Some operations can generate warnings in addition to errors. Warnings are also represented by <legacyBold>Error</legacyBold> objects in the <legacyBold>Errors</legacyBold> collection. When a provider adds a warning to the collection, it does not generate a run-time error. Check the <legacyBold>Count</legacyBold> property of the <legacyBold>Errors</legacyBold> collection to determine whether a warning was produced by a particular operation. If the count is one or greater, an <legacyBold>Error</legacyBold> object has been added to the collection. As soon as you have determined that the <legacyBold>Errors</legacyBold> collection contains errors or warnings, you can iterate through the collection and retrieve information about each <legacyBold>Error</legacyBold> object that it contains. The following short Visual Basic example demonstrates this:</para>
      <code>' BeginErrorHandlingVB02
Private Function DeleteCustomer(ByVal CompanyName As String) As Long
    On Error GoTo DeleteCustomerError
    
    rst.Find "CompanyName='" &amp; CompanyName &amp; "'"
DeleteCustomerError:
Dim objError As ADODB.Error
Dim strError As String

    If cnn.Errors.Count &gt; 0 Then
        For Each objError In cnn.Errors
            strError = strError &amp; "Error #" &amp; objError.Number &amp; _
                " " &amp; objError.Description &amp; vbCrLf &amp; _
                "NativeError: " &amp; objError.NativeError &amp; vbCrLf &amp; _
                "SQLState: " &amp; objError.SQLState &amp; vbCrLf &amp; _
                "Reported by: " &amp; objError.Source &amp; vbCrLf &amp; _
                "Help file: " &amp; objError.HelpFile &amp; vbCrLf &amp; _
                "Help Context ID: " &amp; objError.HelpContext
        Next
        MsgBox strError
    End If
End Function
' EndErrorHandlingVB02</code>
      <para>The error-handling routine includes a <legacyBold>For Each</legacyBold> loop that examines each object in the <legacyBold>Errors</legacyBold> collection. In this example, it accumulates a message for display. In a working program, you would write code to perform an appropriate task for each error, such as closing all open files and shutting down the program in an orderly manner.</para>
    </content>
  </section>
  <section>
    <title>The Error Object</title>
    <content>
      <para>By examining an <legacyBold>Error</legacyBold> object you can determine what error occurred, and more important, what application or what object caused the error. The <legacyBold>Error</legacyBold> object has the following properties:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Property name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>Description</legacyBold>             </para>
            </TD>
            <TD>
              <para>A text description of the error that occurred.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>HelpContext, HelpFile</legacyBold>             </para>
            </TD>
            <TD>
              <para>Refers to the Help topic and Help file that contain a description of the error that occurred.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>NativeError</legacyBold>             </para>
            </TD>
            <TD>
              <para>The provider-specific error number.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Number</legacyBold>             </para>
            </TD>
            <TD>
              <para>A Long Integer that represents the number (listed in the <legacyBold>ErrorValueEnum</legacyBold>) of the error that occurred.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Source</legacyBold>             </para>
            </TD>
            <TD>
              <para>Indicates the name of the object or application that generated an error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>SQLState</legacyBold>             </para>
            </TD>
            <TD>
              <para>A five-character error code that the provider returns during the <?Comment jrs: processing? 2006-06-26T11:22:00Z  Id='0?>process <?CommentEnd Id='0'
    ?>of an SQL statement.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The ADO <legacyBold>Error</legacyBold> object is very similar to the standard Visual Basic <legacyBold>Err</legacyBold> object. Its properties describe the error that occurred. In addition to the number of the error, you also receive two related pieces of information. The <legacyBold>NativeError</legacyBold> property contains an error number specific to the provider you are using. In the previous example, the provider is the Microsoft OLE DB Provider for SQL Server, so <legacyBold>NativeError</legacyBold> will contain errors specific to SQL Server. The <legacyBold>SQLState</legacyBold> property has a five-letter code that describes an error in an SQL statement.</para>
    </content>
  </section>
  <section>
    <title>Event-Related Errors</title>
    <content>
      <para>The <legacyBold>Error</legacyBold> object is also used when event-related errors occur. You can determine whether an error occurred in the process that raised an ADO event by checking the <legacyBold>Error</legacyBold> object passed as an event parameter.</para>
      <para>If the operation that causes an event is concluded successfully, the <legacyItalic>adStatus</legacyItalic> parameter of the event handler will be set to <legacyItalic>adStatusOK</legacyItalic>. On the other hand, if the operation that raised the event was unsuccessful, the <legacyItalic>adStatus</legacyItalic> parameter is set to <legacyItalic>adStatusErrorsOccurred</legacyItalic>. In that case, the <legacyItalic>pError</legacyItalic> parameter will contain an <legacyBold>Error</legacyBold> object that describes the error.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>