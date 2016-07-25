---
title: "The Fields Collection"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 574cf36e-e5f5-403b-983c-749ef93c108f
caps.latest.revision: 11
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
# The Fields Collection
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>Fields</legacyBold> collection is one of ADO's intrinsic collections. A collection is an ordered set of items that can be referred to as a unit. For more information about ADO collections, see <legacyLink xlink:href="7a745aae-9372-49b6-8dae-b9c93e5f3216">The ADO Object Model</legacyLink>.</para>
    <para>The <legacyBold>Fields</legacyBold> collection contains a <legacyBold>Field</legacyBold> object for every field (column) in the <legacyBold>Recordset</legacyBold>. Like all ADO collections, it has <legacyBold>Count</legacyBold> and <legacyBold>Item</legacyBold> properties, as well as <legacyBold>Append</legacyBold> and <legacyBold>Refresh</legacyBold> methods. It also has <legacyBold>CancelUpdate</legacyBold>, <legacyBold>Delete</legacyBold>, <legacyBold>Resync</legacyBold>, and <legacyBold>Update</legacyBold> methods, which are not available to other ADO collections.</para>
  </introduction>
  <section>
    <title>Examining the Fields Collection</title>
    <content>
      <para>Consider the <legacyBold>Fields</legacyBold> collection of the sample <legacyBold>Recordset</legacyBold> introduced in this section. The sample <legacyBold>Recordset</legacyBold> was derived from the SQL statement</para>
      <code>SELECT ProductID, ProductName, UnitPrice FROM Products WHERE CategoryID = 7</code>
      <para>Thus, you should find that the <legacyBold>Recordset</legacyBold> <legacyBold>Fields</legacyBold> collection contains three fields.</para>
      <code>'BeginWalkFields
    Dim objFields As ADODB.Fields
    Dim intLoop As Integer
    
    objRs.Open strSQL, strConnStr, adOpenForwardOnly, adLockReadOnly, adCmdText
    
    Set objFields = objRs.Fields
    
    For intLoop = 0 To (objFields.Count - 1)
        Debug.Print objFields.Item(intLoop).Name
    Next
'EndWalkFields</code>
      <para>This code simply determines the number of <legacyBold>Field</legacyBold> objects in the <legacyBold>Fields</legacyBold> collection using the <legacyBold>Count</legacyBold> property and loops through the collection, returning the value of the <legacyBold>Name</legacyBold> property for each <legacyBold>Field</legacyBold> object. You can use many more <legacyBold>Field</legacyBold> properties to get information about a field. For more information about querying a <legacyBold>Field</legacyBold>, see <legacyLink xlink:href="7d1c4ad5-4be3-42ab-b516-e7133ca300bc">The Field Object</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Counting Columns</title>
    <content>
      <para>As you might expect, the <legacyBold>Count</legacyBold> property returns the actual number of <legacyBold>Field</legacyBold> objects in the <legacyBold>Fields</legacyBold> collection. Because numbering for members of a collection begins with zero, you should always code loops starting with the zero member and ending with the value of the <legacyBold>Count</legacyBold> property minus 1. If you are using Microsoft Visual Basic and want to loop through the members of a collection without checking the <legacyBold>Count</legacyBold> property, use the <legacyBold>For</legacyBold> <legacyBold>Each...Next</legacyBold> command.</para>
      <para>If the <legacyBold>Count</legacyBold> property is zero, there are no objects in the collection.</para>
    </content>
  </section>
  <section>
    <title>Getting to the Field</title>
    <content>
      <para>As with any ADO collection, the <legacyBold>Item</legacyBold> property is the default property of the collection. It returns the individual <legacyBold>Field</legacyBold> object specified by the name or index passed to it. Therefore, the following statements are equivalent for the sample <legacyBold>Recordset</legacyBold>:</para>
      <code>objField = objRecordset.Fields.Item("ProductID")
objField = objRecordset.Fields("ProductID")
objField = objRecordset.Fields.Item(0)
objField = objRecordset.Fields(0)</code>
      <para>If these methods are equivalent, which is best? It depends. Using an index to retrieve a <legacyBold>Field</legacyBold> from the collection is faster because it accesses the <legacyBold>Field</legacyBold> directly without having to perform a string lookup. On the other hand, the order of <legacyBold>Fields</legacyBold> within the collection must be known, and if the order changes, the reference to the <legacyBold>Field's</legacyBold> index will have to be changed wherever it occurs. Although slightly slower, using the name of the <legacyBold>Field</legacyBold> is more flexible because it doesn't depend on the order of the <legacyBold>Fields</legacyBold> in the collection.</para>
    </content>
  </section>
  <section>
    <title>Using the Refresh Method</title>
    <content>
      <para>Unlike some other ADO collections, using the <legacyBold>Refresh</legacyBold> method on the <legacyBold>Fields</legacyBold> collection has no visible effect. To retrieve changes from the underlying database structure, you must use either the <legacyBold>Requery</legacyBold> method, or if the <legacyBold>Recordset</legacyBold> object does not support bookmarks, the <legacyBold>MoveFirst</legacyBold> method, which will cause the command to be executed against the provider again.</para>
    </content>
  </section>
  <section>
    <title>Adding Fields to a Recordset</title>
    <content>
      <para>The <legacyBold>Append</legacyBold> method is used to add fields to a <legacyBold>Recordset</legacyBold>. </para>
      <para>You can use the <legacyBold>Append</legacyBold> method to fabricate a <legacyBold>Recordset</legacyBold> programmatically without opening a connection to a data source. A run-time error will occur if the <legacyBold>Append</legacyBold> method is called on the <legacyBold>Fields</legacyBold> collection of an open <legacyBold>Recordset</legacyBold> or on a <legacyBold>Recordset</legacyBold> where the <legacyBold>ActiveConnection</legacyBold> property has been set. You can append fields only to a <legacyBold>Recordset</legacyBold> that is not open and has not yet been connected to a data source. However, to specify values for the newly appended <legacyBold>Fields</legacyBold>, the <legacyBold>Recordset</legacyBold> must first be opened.</para>
      <para>Developers often need a place to temporarily store some data, or want some data to act as if it came from a server so it can participate in data binding in a user interface. ADO (in conjunction with the <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Microsoft Cursor Service for OLE DB</legacyLink>) enables the developer to build an empty <legacyBold>Recordset</legacyBold> object by specifying column information and calling <legacyBold>Open</legacyBold>. In the following example, three new fields are appended to a new <legacyBold>Recordset</legacyBold> object. Then the <legacyBold>Recordset</legacyBold> is opened, two new records are added, and the <legacyBold>Recordset</legacyBold> is persisted to a file. (For more information about <legacyBold>Recordset</legacyBold> persistence, see <legacyLink xlink:href="8dc27274-4f96-43d1-913c-4ff7d01b9a27">Updating and Persisting Data</legacyLink>.)</para>
      <code>'BeginFabricate
    Dim objRs As ADODB.Recordset
    Set objRs = New ADODB.Recordset
    
    With objRs.Fields
        .Append "StudentID", adChar, 11, adFldUpdatable
        .Append "FullName", adVarChar, 50, adFldUpdatable
        .Append "PhoneNmbr", adVarChar, 20, adFldUpdatable
    End With
    
    With objRs
        .Open
        
        .AddNew
        .Fields(0) = "123-45-6789"
        .Fields(1) = "John Doe"
        .Fields(2) = "(425) 555-5555"
        .Update
        
        .AddNew
        .Fields(0) = "123-45-6780"
        .Fields(1) = "Jane Doe"
        .Fields(2) = "(615) 555-1212"
        .Update
    End With
            
    objRs.Save App.Path &amp; "FabriTest.adtg", adPersistADTG
    
    objRs.Close
'EndFabricate</code>
      <para>The usage of the <legacyBold>Fields</legacyBold> <legacyBold>Append</legacyBold> method differs between the <legacyBold>Recordset</legacyBold> object and the <legacyBold>Record</legacyBold> object. For more information about the <legacyBold>Record</legacyBold> object, see <legacyLink xlink:href="4d68868e-2611-4b5c-9a89-7caa5f753151">Records and Streams</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="a584e642-a4a3-418e-bc20-3aff81a5625a">Fabricating Hierarchical Recordsets</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>