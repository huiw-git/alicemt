---
title: "ADO Properties"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ac0d1a7-6c7a-4f4c-b115-428935e0f98b
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
# ADO Properties
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates on which page the current record resides.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates the ordinal position of the current record of a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates the <legacyBold>Command</legacyBold> object that created the associated <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates to which <legacyBold>Connection</legacyBold> object the specified <legacyBold>Command</legacyBold>, <legacyBold>Recordset</legacyBold>, or <legacyBold>Record</legacyBold> object currently belongs.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates the actual length of a field's value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates one or more characteristics of an object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF and EOF</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <legacyBold>BOF</legacyBold> indicates that the current record position is before the first record in a Recordset object.</para>
            <para>
              <legacyBold>EOF</legacyBold> indicates that the current record position is after the last record in a Recordset object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates a bookmark that uniquely identifies the current record in a <legacyBold>Recordset</legacyBold> object or sets the current record in a <legacyBold>Recordset</legacyBold> object to the record identified by a valid bookmark.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates the number of records from a <legacyBold>Recordset</legacyBold> object that are cached locally in memory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="8aa90cb0-f588-4141-9dc9-3b22918394ee">Chapter</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Gets or sets an OLE DB <legacyBold>Chapter</legacyBold> object from/on an <legacyBold>ADORecordsetConstruction</legacyBold> object. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="e42507cb-9b46-4ce4-8191-2948eaf14ca2">CharSet</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates the character set into which the contents of a text <legacyBold>Stream</legacyBold> should be translated.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates the stream used as the input to a <legacyBold>Command</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Indicates the text of a command to be issued against a provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates how long to wait while executing a command before terminating the attempt and generating an error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the type of a <legacyBold>Command</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the information used to establish a connection to a data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates how long to wait while establishing a connection before terminating the attempt and generating an error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the number of objects in a collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the location of the cursor service.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the type of cursor used in a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="2c8fb09e-10ad-49b5-ab41-2603771780d9">DataMember</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the name of the data member that will be retrieved from the object referenced by the <legacyBold>DataSource</legacyBold> property.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="300a702a-3544-48c5-b759-83b511fe97e0">DataSource</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates an object that contains data to be represented as a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="41e8a8dd-e69c-4a09-8736-93502e01961c">DefaultDatabase</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the default database for a <legacyBold>Connection</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the data capacity of a <legacyBold>Field</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description</legacyLink> </para>
          </TD>
          <TD>
            <para>Describes an <legacyBold>Error</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="329c3a71-ba88-4009-b04f-2f52195a5957">Dialect</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the syntax and general rules that the provider will use to parse the <legacyBold>CommandText</legacyBold> or <legacyBold>CommandStream</legacyBold> properties.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates whether the <legacyBold>Parameter</legacyBold> represents an input parameter, an output parameter, or both, or if the parameter is the return value from a stored procedure.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the editing status of the current record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates whether the current position is at the end of the stream.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates a filter for data in a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext and HelpFile</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the Help file and topic associated with an <legacyBold>Error</legacyBold> object.</para>
            <para>
              <legacyBold>HelpContextID</legacyBold> returns a context ID, as a <legacyBold>Long</legacyBold> value, for a topic in a Help file.</para>
            <para>
              <legacyBold>HelpFile</legacyBold> returns a <legacyBold>String</legacyBold> value that evaluates to a fully resolved path of a Help file.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the name of the index currently in effect for a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ea84e4b2-fbf2-4eef-b9ce-796b22e21800">IsolationLevel</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the level of isolation for a <legacyBold>Connection</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates a specific member of a collection, by name or ordinal number.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0b20fbb8-6b83-48ec-b442-f96c8a4bafbb">LineSeparator</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the binary character to be used as the line separator in text <legacyBold>Stream</legacyBold> objects.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the type of locks placed on records during editing.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="390c8abf-133e-40da-8b99-8f748a983e4f">MarshalOptions</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates which records are to be marshaled back to the server.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the maximum number of records to return to a <legacyBold>Recordset</legacyBold> from a query.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the available permissions for modifying data in a <legacyBold>Connection</legacyBold>, <legacyBold>Record</legacyBold>, or <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the name of an object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the provider-specific error code for a particular <legacyBold>Error</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the number that uniquely identifies an <legacyBold>Error</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the scale of numeric values in a <legacyBold>Parameter</legacyBold> or <legacyBold>Field</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the value of a <legacyBold>Field</legacyBold> that existed in the record before any changes were made.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates how many pages of data the <legacyBold>Recordset</legacyBold> object contains.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates how many records represent one page in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="5ea8029b-eda4-490b-ae84-2ad036fb582f">ParentRow</legacyLink> </para>
          </TD>
          <TD>
            <para>Sets the container of an OLE DB <legacyBold>Row</legacyBold> object on an <legacyBold>ADORecordConstruction</legacyBold> object, so that the parent of the row is turned into an ADO <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="65120ce6-3900-4cd4-b322-3b9816d74737">ParentURL</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates an absolute URL string that points to the parent <legacyBold>Record</legacyBold> of the current <legacyBold>Record</legacyBold> object. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the current position within a <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the degree of precision for numeric values in a <legacyBold>Parameter</legacyBold> object or for numeric <legacyBold>Field</legacyBold> objects.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates whether to save a compiled version of a command before execution.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the name of the provider for a <legacyBold>Connection</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the number of records in a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="790e46a2-13d2-451e-a8be-130bd9a206a4">RecordType</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the type of <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="21019d89-2dd1-4a26-ac6f-384b81d66949">Row</legacyLink> </para>
          </TD>
          <TD>
            <para>Gets or sets an OLE DB <legacyBold>Row</legacyBold> object from/on an <legacyBold>ADORecordConstruction</legacyBold> object. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="9d068fed-39bf-4842-afc3-686a2af2145d">RowPosition</legacyLink> </para>
          </TD>
          <TD>
            <para>Gets or sets an OLE DB <legacyBold>RowPosition</legacyBold> object from/on an <legacyBold>ADORecordsetConstruction</legacyBold> object. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="7d359294-4ff2-47e0-8111-0c221b24d80e">Rowset</legacyLink> </para>
          </TD>
          <TD>
            <para>Gets or sets an OLE DB <legacyBold>Rowset</legacyBold> object from/on an <legacyBold>ADORecordsetConstruction</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source (ADO Error)</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the name of the object or application that originally generated an error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source (ADO Record)</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the entity represented by the <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source (ADO Recordset)</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the source for the data in a <legacyBold>Recordset</legacyBold> object </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the SQL state for a specific <legacyBold>Error</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates for all applicable objects whether the state of the object is open or closed. Indicates for all applicable objects executing an asynchronous method, whether the current state of the object is connecting, executing, or retrieving</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">Status (ADO Field)</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the status of a <legacyBold>Field</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status (ADO Recordset)</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the status of the current record regarding batch updates or other bulk operations.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="502d69b5-dc9a-455d-b115-a03bd39a552b">StayInSync</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates, in a hierarchical <legacyBold>Recordset</legacyBold> object, whether the reference to the underlying child records (that is, the <legacyItalic>chapter</legacyItalic>) changes when the parent row position changes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="4a44f9f6-0265-4c00-8def-d85b6af923b1">Stream Property</link>
            </para>
          </TD>
          <TD>
            <para>Gets or sets an OLE DB <legacyBold>Stream</legacyBold> object from/on an <legacyBold>ADOStreamConstruction</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the operational type or data type of a <legacyBold>Parameter</legacyBold>, <legacyBold>Field</legacyBold>, or <legacyBold>Property</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type (ADO Stream)</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the type of data that is contained in the <legacyBold>Stream</legacyBold> (binary or text).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the current value in the database for a <legacyBold>Field</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the value assigned to a <legacyBold>Field</legacyBold>, <legacyBold>Parameter</legacyBold>, or <legacyBold>Property</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="db4cb894-9bd9-422d-a58a-cef6941a5784">Version</legacyLink> </para>
          </TD>
          <TD>
            <para>Indicates the ADO version number.</para>
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
<link xlink:href="0ce201c3-6657-4c87-ae81-0d7dc5b5a431">Appendix B: ADO Errors</link>
<link xlink:href="0ded5ad9-8f83-4224-95af-38512783b972">ADO Events</link>
<link xlink:href="a38c5670-ba28-44f3-bd5b-fcb46880e904">ADO Methods</link>
<link xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</link>
<link xlink:href="d0b7e254-c89f-4406-b846-a060ef038c30">ADO Objects</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>