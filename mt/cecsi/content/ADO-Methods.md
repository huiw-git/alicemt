---
title: "ADO Methods"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a38c5670-ba28-44f3-bd5b-fcb46880e904
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
# ADO Methods
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Creates a new record for an updatable <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Appends an object to a collection. If the collection is <legacyBold>Fields</legacyBold>, a new <legacyBold>Field</legacyBold> object may be created before it is appended to the collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Appends data to a large text or binary data <legacyBold>Field</legacyBold>, or to a <legacyBold>Parameter</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans, CommitTrans, and RollbackTrans</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Manages transaction processing within a <legacyBold>Connection</legacyBold> object as follows:</para>
            <para>
              <legacyBold>BeginTrans</legacyBold> — Begins a new transaction.</para>
            <para>
              <legacyBold>CommitTrans</legacyBold> — Saves any changes and ends the current transaction. It may also start a new transaction.</para>
            <para>
              <legacyBold>RollbackTrans</legacyBold> — Cancels any changes and ends the current transaction. It may also start a new transaction.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Cancels execution of a pending, asynchronous method call.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Cancels a pending batch update.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Cancels any changes that were made to the current or new row of a <legacyBold>Recordset</legacyBold> object, or the <legacyBold>Fields</legacyBold> collection of a <legacyBold>Record</legacyBold> object, before calling the <legacyBold>Update</legacyBold> method.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Removes all the <legacyBold>Error</legacyBold> objects from the <legacyBold>Errors</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Creates a duplicate <legacyBold>Recordset </legacyBold>object from an existing <legacyBold>Recordset</legacyBold> object. Optionally, specifies that the clone be read-only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Closes an open object and any dependent objects.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6">CompareBookmarks</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Compares two bookmarks and returns an indication of their relative values.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b9bcf272-3c74-479f-95dd-0229a32e98fc">CopyRecord</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Copies a file or directory, and its contents, to another location. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b4aa5714-916b-48b8-8b09-cc2708379602">CopyTo</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Copies the specified number of characters or bytes (depending on <legacyBold>Type</legacyBold>) in the <legacyBold>Stream</legacyBold> to another <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Creates a new <legacyBold>Parameter</legacyBold> object that has the specified properties.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete (ADO Parameters Collection)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Deletes an object from the <legacyBold>Parameters</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="25bedc25-c51c-4cab-96ce-930b959965d9">Delete (ADO Fields Collection)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Deletes an object from the <legacyBold>Fields</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete (ADO Recordset)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Deletes the current record or a group of records.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="2726498c-dbd8-4266-983b-ae7d62c39142">DeleteRecord</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Deletes a file or directory, and all its subdirectories.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute (ADO Command)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Executes the query, SQL statement, or stored procedure specified in the <legacyBold>CommandText</legacyBold> property.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute (ADO Connection)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Executes the specified query, SQL statement, stored procedure, or provider-specific text.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Searches a <legacyBold>Recordset</legacyBold> for the row that satisfies the specified criteria.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="938522b4-f836-4c80-8d27-a598a000f0ee">Flush</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Forces the contents of the <legacyBold>Stream</legacyBold> remaining in the ADO buffer to the underlying object with which the <legacyBold>Stream</legacyBold> is associated.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="23d551f5-3d5b-434b-ade6-fef15f1710e7">get_OLEDBCommand</link>
            </para>
          </TD>
          <TD>
            <para>Returns the underlying OLEDB Command, first propagating any parameter information set on the ADO Command to the OLEDB command.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b3f09bac-4f66-49f6-aa5a-6fbb4fb28338">GetChildren</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Returns a <legacyBold>Recordset</legacyBold> whose rows represent the files and subdirectories in the directory represented by this <legacyBold>Record</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Returns all, or a portion of, the contents of a large text or binary data <legacyBold>Field</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="5a4c6bd5-0c79-4f81-a977-0561392d8d50">GetDataProviderDSO</link>
            </para>
          </TD>
          <TD>
            <para>Retrieves the underlying OLEDB Data Source object from the Shape provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Retrieves multiple records of a <legacyBold>Recordset</legacyBold> object into an array.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Returns the <legacyBold>Recordset</legacyBold> as a string.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b18d8d38-7354-4a94-b637-6ac035faa433">LoadFromFile</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Loads the contents of an existing file into a <legacyBold>Stream</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Moves the position of the current record in a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Moves to the first, last, next, or previous record in a specified <legacyBold>Recordset</legacyBold> object and makes that record the current record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Moves a file, or a directory and its contents, to another location. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Clears the current <legacyBold>Recordset</legacyBold> object and returns the next <legacyBold>Recordset</legacyBold> by advancing through a series of commands.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open (ADO Connection)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Opens a connection to a data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open (ADO Record)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Opens an existing <legacyBold>Record</legacyBold> object, or creates a new file or directory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open (ADO Recordset)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Opens a cursor.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open (ADO Stream)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Opens a <legacyBold>Stream</legacyBold> object to manipulate streams of binary or text data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Obtains database schema information from the provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="ca6a5804-bf5c-4afc-99db-22904bc0b33d">put_OLEDBCommand</link>
            </para>
          </TD>
          <TD>
            <para>This method performs no operation - it always returns S_OK.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="838502de-80f1-4eeb-8838-dd3d9403e567">Read</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Reads a specified number of bytes from a <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="be5a409e-cf87-4859-9ea5-713401755a77">ReadText</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Reads a specified number of characters from a text <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Updates the objects in a collection to reflect objects available from, and specific to, the provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Updates the data in a <legacyBold>Recordset</legacyBold> object by re-executing the query on which the object is based.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Refreshes the data in the current <legacyBold>Recordset</legacyBold> object, or <legacyBold>Fields</legacyBold> collection of a <legacyBold>Record</legacyBold> object, from the underlying database.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Saves the <legacyBold>Recordset</legacyBold> in a file or <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="8a8594f2-422b-4d2e-94f8-7fe337445900">SaveToFile</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Saves the binary contents of a <legacyBold>Stream</legacyBold> to a file.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Searches the index of a <legacyBold>Recordset</legacyBold> to quickly locate the row that matches the specified values, and changes the current row position to that row.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Sets the position that is the end of the stream.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329">SkipLine</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Skips one entire line when reading a text stream.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="99a2b2d4-e6b1-4205-b011-72d024ea7240">Stat</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Gets statistical information about an open stream.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Determines whether a specified <legacyBold>Recordset</legacyBold> object supports a particular type of functionality.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Saves any changes you make to the current row of a <legacyBold>Recordset</legacyBold> object, or the <legacyBold>Fields</legacyBold> collection of a <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Writes all pending batch updates to disk.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Writes binary data to a <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Writes a specified text string to a <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="bfd96a4b-c913-45aa-9e4c-ec86ac364f3a">ADO API Reference</link>
<link xlink:href="b5e1d26d-b41d-4e35-8c7c-972426473dfb">ADO Collections</link>
<link xlink:href="d7b06d72-f792-4328-93a2-5006b9e2c581">ADO Dynamic Properties</link>
<link xlink:href="c97ed131-1a93-463c-9e61-22f029b0c474">ADO Enumerated Constants</link>
<link xlink:href="0ce201c3-6657-4c87-ae81-0d7dc5b5a431">ADO Errors</link>
<link xlink:href="0ded5ad9-8f83-4224-95af-38512783b972">ADO Events</link>
<link xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</link>
<link xlink:href="d0b7e254-c89f-4406-b846-a060ef038c30">ADO Objects</link>
<link xlink:href="0ac0d1a7-6c7a-4f4c-b115-428935e0f98b">ADO Properties</link>
</relatedTopics>
</developerOrientationDocument>