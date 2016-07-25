---
title: "Detecting and Resolving Conflicts"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b28fdd26-c1a4-40ce-a700-2b0c9d201514
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
# Detecting and Resolving Conflicts
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If you are dealing with your Recordset in immediate mode, there is much less chance for concurrency problems to occur. On the other hand, if your application uses batch mode updating, there may be a good chance that one user will change a record before changes that were made by another user editing the same record are saved. In such a case, you will want your application to gracefully handle the conflict. It may be your wish that the last person to send an update to the server "wins." Or you may want to let the most recent user to decide which update should take precedence by providing him with a choice between the two conflicting values.</para>
    <para>Whatever the case, ADO provides the UnderlyingValue and OriginalValue properties of the Field object to handle these types of conflicts. Use these properties in combination with the Resync method and Filter property of the Recordset.</para>
  </introduction>
  <section>
    <title>Remarks</title>
    <content>
      <para>When ADO encounters a conflict during a batch update, a warning will be added to the Errors collection. Therefore, you should always check for errors immediately after you call BatchUpdate, and if you find them, begin testing the assumption that you have encountered a conflict. The first step is to set the Filter property on the Recordset equal to adFilterConflictingRecords. This limits the view on your Recordset to only those records that are in conflict. If the RecordCount property is equal to zero after this step, you know the error was raised by something other than a conflict.</para>
      <para>When you call BatchUpdate, ADO and the provider are generating SQL statements to perform updates on the data source. Remember that certain data sources have limitations on which types of columns can be used in a WHERE clause.</para>
      <para>Next, call the Resync method on the Recordset with the AffectRecords argument set equal to adAffectGroup and the ResyncValues argument set equal to adResyncUnderlyingValues. The Resync method updates the data in the current Recordset object from the underlying database. By using adAffectGroup, you are ensuring that only the records visible with the current filter setting, that is, only the conflicting records, are resynchronized with the database. This could make a significant performance difference if you are dealing with a large Recordset. By setting the ResyncValues argument to adResyncUnderlyingValues when calling Resync, you ensure that the UnderlyingValue property will contain the (conflicting) value from the database, that the Value property will maintain the value entered by the user, and that the OriginalValue property will hold the original value for the field (the value it had before the last successful UpdateBatch call was made). You can then use these values to resolve the conflict programmatically or require the user to select the value that will be used.</para>
      <para>This technique is shown in the following code example. The example artificially creates a conflict by using a separate Recordset to change a value in the underlying table before UpdateBatch is called.</para>
      <code>'BeginConflicts
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" &amp; _
              "Data Source=MySQLServer;Integrated Security=SSPI;"
             
    strSQL = "SELECT * FROM Shippers WHERE ShipperID = 2"
                 
    'Open Rs and change a value
    Set objRs1 = New ADODB.Recordset
    Set objRs2 = New ADODB.Recordset
    objRs1.CursorLocation = adUseClient
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText
    objRs1("Phone") = "(111) 555-1111"
    
    'Introduce a conflict at the db...
    objRs2.Open strSQL, strConn, adOpenKeyset, adLockOptimistic, adCmdText
    objRs2("Phone") = "(999) 555-9999"
    objRs2.Update
    objRs2.Close
    Set objRs2 = Nothing
    
    On Error Resume Next
    objRs1.UpdateBatch
    
    If objRs1.ActiveConnection.Errors.Count &lt;&gt; 0 Then
        Dim intConflicts As Integer
        
        intConflicts = 0
        
        objRs1.Filter = adFilterConflictingRecords
        
        intConflicts = objRs1.RecordCount
        
        'Resync so we can see the UnderlyingValue and offer user a choice.
        'This sample only displays all three values and resets to original.
        objRs1.Resync adAffectGroup, adResyncUnderlyingValues
        
        If intConflicts &gt; 0 Then
            strMsg = "A conflict occurred with updates for " &amp; intConflicts &amp; _
                     " record(s)." &amp; vbCrLf &amp; "The values will be restored" &amp; _
                     " to their original values." &amp; vbCrLf &amp; vbCrLf
                     
            objRs1.MoveFirst
            While Not objRs1.EOF
              strMsg = strMsg &amp; "SHIPPER = " &amp; objRs1("CompanyName") &amp; vbCrLf
              strMsg = strMsg &amp; "Value = " &amp; objRs1("Phone").Value &amp; vbCrLf
              strMsg = strMsg &amp; "UnderlyingValue = " &amp; _
                                 objRs1("Phone").UnderlyingValue &amp; vbCrLf
              strMsg = strMsg &amp; "OriginalValue = " &amp; _
                                 objRs1("Phone").OriginalValue &amp; vbCrLf
              strMsg = strMsg &amp; vbCrLf &amp; "Original value has been restored."
                
              MsgBox strMsg, vbOKOnly, _
                    "Conflict " &amp; objRs1.AbsolutePosition &amp; _
                    " of " &amp; intConflicts
                
              objRs1("Phone").Value = objRs1("Phone").OriginalValue
              objRs1.MoveNext
            Wend
            
            objRs1.UpdateBatch adAffectGroup
        Else
            'Other error occurred. Minimal handling in this example.
             strMsg = "Errors occurred during the update. " &amp; _
                        objRs1.ActiveConnection.Errors(0).Number &amp; " " &amp; _
                        objRs1.ActiveConnection.Errors(0).Description
        End If
        
        On Error GoTo 0
    End If
    
    objRs1.MoveFirst
    objRs1.Close
    Set objRs1 = Nothing
'EndConflicts</code>
      <para>You can use the Status property of the current Record or of a specific Field to determine what kind of a conflict has occurred.</para>
      <para>For detailed information about error handling, see <link xlink:href="4909e413-f3b0-4183-8ad3-67b1434df742">Error Handling</link>.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="0cb548e0-fcb4-4c49-98c8-be287911f826">Batch Mode</link>
</relatedTopics>
</developerConceptualDocument>