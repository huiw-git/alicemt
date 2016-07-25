---
title: "Comments on HelloData"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a2831d77-7040-4b73-bbae-fe0bf78107ed
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
# Comments on HelloData
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The HelloData application steps through the basic operations of a typical ADO application: getting, examining, editing, and updating data. When you start the application, click the first button, <legacyBold>Get Data</legacyBold>. This will run the <legacyBold>GetData</legacyBold> subroutine. </para>
  </introduction>
  <section>
    <title>GetData</title>
    <content>
      <para>
        <legacyBold>GetData</legacyBold> places a valid connection string into a module-level variable, <legacyItalic>m_sConnStr</legacyItalic>. For more information about connection strings, see <legacyLink xlink:href="14eae122-2d1e-40c8-b88e-b7cb8dfbc93b">Creating the Connection String</legacyLink>.</para>
      <para>Assign an error handler using a Visual Basic <legacyBold>OnError</legacyBold> statement. For more information about error handling in ADO, see <legacyLink xlink:href="4909e413-f3b0-4183-8ad3-67b1434df742">Error Handling</legacyLink>. A new <legacyBold>Connection</legacyBold> object is created, and the <legacyBold>CursorLocation</legacyBold> property is set to <legacyBold>adUseClient</legacyBold> because the HelloData example creates a <legacyItalic>disconnected Recordset</legacyItalic>. This means that as soon as the data has been fetched from the data source, the physical connection with the data source is broken, but you can still work with the data that is cached locally in your <legacyBold>Recordset</legacyBold> object.</para>
      <para>After the connection has been opened, assign an SQL string to a variable (sSQL). Then create an instance of a new <legacyBold>Recordset</legacyBold> object, <codeInline>m_oRecordset1</codeInline>. In the next line of code, open the <legacyBold>Recordset</legacyBold> over the existing <legacyBold>Connection</legacyBold>, passing in <codeInline>sSQL</codeInline> as the source of the <legacyBold>Recordset</legacyBold>. You help ADO in making the determination that the SQL string you have passed as the source for the <legacyBold>Recordset</legacyBold> is a textual definition of a command by passing <legacyBold>adCmdText</legacyBold> in the final argument to the <legacyBold>Recordset</legacyBold> <legacyBold>Open</legacyBold> method. This line also sets the <legacyBold>LockType</legacyBold> and <legacyBold>CursorType</legacyBold> associated with the <legacyBold>Recordset</legacyBold>.</para>
      <para>The next line of code sets the <legacyBold>MarshalOptions</legacyBold> property equal to <legacyBold>adMarshalModifiedOnly</legacyBold>. <legacyBold>MarshalOptions</legacyBold> indicates which records should be marshaled to the middle tier (or Web server). For more information about marshaling, see the COM documentation. When you use <legacyBold>adMarshalModifiedOnly</legacyBold> with a client-side cursor (<legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> = <legacyBold>adUseClient</legacyBold>), only records that have been modified on the client are written back to the middle tier. Setting <legacyBold>MarshalOptions</legacyBold> to <legacyBold>adMarshalModifiedOnly</legacyBold> can improve performance because fewer rows are marshaled.</para>
      <para>Next, disconnect the <legacyBold>Recordset</legacyBold> by setting its <legacyBold>ActiveConnection</legacyBold> property equal to <legacyBold>Nothing</legacyBold>. For more information, see the section "Disconnecting and Reconnecting the Recordset" in <link xlink:href="8dc27274-4f96-43d1-913c-4ff7d01b9a27">Updating and Persisting Data</link>.</para>
      <para>Close the connection to the data source and destroy the existing <legacyBold>Connection</legacyBold> object. This releases the resources that it consumed.</para>
      <para>The final step is to set the <legacyBold>Recordset</legacyBold> as the <legacyBold>DataSource</legacyBold> for the Microsoft DataGrid Control on the form so that you can easily display the data from the <legacyBold>Recordset</legacyBold> on the form.</para>
      <para>Click the second button, <legacyBold>Examine Data</legacyBold>. This runs the <legacyBold>ExamineData</legacyBold> subroutine.</para>
    </content>
  </section>
  <section>
    <title>ExamineData</title>
    <content>
      <para>ExamineData uses various methods and properties of the <legacyBold>Recordset</legacyBold> object to display information about the data in the <legacyBold>Recordset</legacyBold>. It reports the number of records by using the <legacyBold>RecordCount</legacyBold> property. It loops through the <legacyBold>Recordset</legacyBold> and prints the value of the <legacyBold>AbsolutePosition</legacyBold> property in the display text box on the form. Also while in the loop, the value of the <legacyBold>Bookmark</legacyBold> property for the third record is placed into a variant variable, <legacyItalic>vBookmark</legacyItalic>, for later use.</para>
      <para>The routine navigates directly back to the third record using the bookmark variable that it stored earlier. The routine calls the <legacyBold>WalkFields</legacyBold> subroutine, which loops through the <legacyBold>Fields</legacyBold> collection of the <legacyBold>Recordset</legacyBold> and displays details about each <legacyBold>Field</legacyBold> in the collection.</para>
      <para>Finally, <legacyBold>ExamineData</legacyBold> uses the <legacyBold>Filter</legacyBold> property of the <legacyBold>Recordset</legacyBold> to screen for only those records with a <legacyBold>CategoryId</legacyBold> equal to 2. The result of applying this filter is immediately visible in the display grid on the form.</para>
      <para>For more information about the functionality shown in the <legacyBold>ExamineData</legacyBold> subroutine, see <legacyLink xlink:href="de1d74af-89b6-4f3f-a8c9-07c3e2b3c9a5">Examining Data</legacyLink>.</para>
      <para>Next, click the third button, <legacyBold>Edit Data</legacyBold>. This will run the <legacyBold>EditData</legacyBold> subroutine.</para>
    </content>
  </section>
  <section>
    <title>EditData</title>
    <content>
      <para>When the code enters the <legacyBold>EditData</legacyBold> subroutine, the <legacyBold>Recordset</legacyBold> is still filtered on <legacyBold>CategoryId</legacyBold> equal to 2, so that only those items that meet the filter criteria are visible. It first loops through the <legacyBold>Recordset</legacyBold> and increases the price of each visible item in the <legacyBold>Recordset</legacyBold> by 10 percent. The value of the <legacyBold>Price</legacyBold> field is changed by setting the <legacyBold>Value</legacyBold> property for that field equal to a new, valid amount.</para>
      <para>Remember that the <legacyBold>Recordset</legacyBold> is disconnected from the data source. The changes that were made in <legacyBold>EditData</legacyBold> are made only to the locally cached copy of the data. For more information, see <legacyLink xlink:href="ef514f85-c446-4f05-824e-c9313b2ffae1">Editing Data</legacyLink>.</para>
      <para>The changes will not be made on the data source until you click the fourth button, <legacyBold>Update Data</legacyBold>. This will run the <legacyBold>UpdateData</legacyBold> subroutine.</para>
    </content>
  </section>
  <section>
    <title>UpdateData</title>
    <content>
      <para>UpdateData first removes the filter that has been applied to the <legacyBold>Recordset</legacyBold>. The code removes and resets <codeInline>m_oRecordset1</codeInline> as the <legacyBold>DataSource</legacyBold> for the Microsoft Bound DataGrid on the form so that the unfiltered <legacyBold>Recordset</legacyBold> appears in the grid.</para>
      <para>The code then checks to see whether you can move backward in the <legacyBold>Recordset</legacyBold> by using the <legacyBold>Supports</legacyBold> method with the <legacyBold>adMovePrevious</legacyBold> argument.</para>
      <para>The routine moves to the first record using the <legacyBold>MoveFirst</legacyBold> method and displays the field's original and current values, by using the <legacyBold>OriginalValue</legacyBold> and <legacyBold>Value</legacyBold> properties of the <legacyBold>Field</legacyBold> object. These properties, together with the <legacyBold>UnderlyingValue</legacyBold> property (not used here), are discussed in <legacyLink xlink:href="8dc27274-4f96-43d1-913c-4ff7d01b9a27">Updating and Persisting Data</legacyLink>.</para>
      <para>Next, a new <legacyBold>Connection</legacyBold> object is created and used to reestablish a connection to the data source. You reconnect the <legacyBold>Recordset</legacyBold> to the data source by setting the new <legacyBold>Connection</legacyBold> as the <legacyBold>ActiveConnection</legacyBold> for the <legacyBold>Recordset</legacyBold>. To send the updates to the server, the code calls <legacyBold>UpdateBatch</legacyBold> on the <legacyBold>Recordset</legacyBold>.</para>
      <para>If the batch update succeeds, a module-level flag variable, <codeInline>m_flgPriceUpdated</codeInline>, is set to True. This will remind you later to clean up all the changes that were made to the database.</para>
      <para>Finally, the code moves back to the first record in the <legacyBold>Recordset</legacyBold> and displays the original and current values. The values are the same after the call to <legacyBold>UpdateBatch</legacyBold>.</para>
      <para>For detailed information about how to update data, including what to do when data on the server changes while your <legacyBold>Recordset</legacyBold> is disconnected, see <legacyLink xlink:href="8dc27274-4f96-43d1-913c-4ff7d01b9a27">Updating and Persisting Data</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Form_Unload</title>
    <content>
      <para>The <legacyBold>Form_Unload</legacyBold> subroutine is important for several reasons. First, because this is a sample application, Form_Unload cleans up the changes that were made to the database before the application exits. Second, the code shows how a command can be executed directly from an open <legacyBold>Connection</legacyBold> object by using the <legacyBold>Execute</legacyBold> method. Finally, it shows an example of executing a non-row–returning query (an UPDATE query) against the data source.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>