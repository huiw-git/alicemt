---
title: "ADO Enumerated Constants"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
caps.latest.revision: 9
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
# ADO Enumerated Constants
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To assist in debugging, the ADO enumerations list a value for each constant. However, this value is purely advisory, and may change from one release of ADO to another. Your code should only depend on the name, not the actual value, of each enumerated constant.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="f0965617-17d8-41e0-98d0-f824274735a6">ADCPROP_ASYNCTHREADPRIORITY_ENUM</legacyLink>             </para>
          </TD>
          <TD>
            <para>For an RDS <legacyBold>Recordset</legacyBold> object, specifies the execution priority of the asynchronous thread that retrieves data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="ded4f087-87b9-4efa-8026-bde53d3e9e8a">ADCPROP_AUTORECALC_ENUM</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies when the <legacyBold>MSDataShape</legacyBold> provider re-calculates aggregate and calculated columns in a hierarchical <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="33fd7b65-2ec8-4f62-91a7-630b5dab1aa2">ADCPROP_UPDATECRITERIA_ENUM</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies which fields can be used to detect conflicts during an optimistic update of a row of the data source with a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="bc9e1a37-e969-47e9-8382-0bbfffa2034f">ADCPROP_UPDATERESYNC_ENUM</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether the <legacyBold>UpdateBatch</legacyBold> method is followed by an implicit <legacyBold>Resync</legacyBold> method operation and if so, the scope of that operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="1ab921a0-6c57-43b4-9291-701b2599f3e8">AffectEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies which records are affected by an operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="55d273c4-ccee-48ef-ba90-8893d04313c8">BookmarkEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies a bookmark that indicates where the operation should begin.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies how a command argument should be interpreted.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="bc8f710d-0621-4673-8d8e-0361e44abed0">CompareEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the relative position of two records represented by their bookmarks.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="3792c294-5161-4538-a908-22a5fc50b85f">ConnectModeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the available permissions for modifying data in a <legacyBold>Connection</legacyBold>, opening a <legacyBold>Record</legacyBold>, or specifying values for the <legacyBold>Mode</legacyBold> property of the<legacyBold> Record</legacyBold> and <legacyBold>Stream</legacyBold> objects.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="bff07eeb-dee3-4e4e-9b2d-d56061ea744d">ConnectOptionEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether the <legacyBold>Open</legacyBold> method of a <legacyBold>Connection</legacyBold> object should return after (synchronously) or before (asynchronously) the connection is established.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="21026e24-62b7-4cc9-8aef-62c1fc6cba75">ConnectPromptEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether a dialog box should be displayed to prompt for missing parameters when opening a connection to an ODBC data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="2fa4eec5-d50b-4fd3-8ae7-40af441ba12b">CopyRecordOptionsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the behavior of the <legacyBold>CopyRecord</legacyBold> method.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="acb255ff-1734-4b70-89bb-aef862b4c63b">CursorLocationEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the location of the cursor engine.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="4e10cda7-ce81-4466-94c2-844d38191cf1">CursorOptionEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies what functionality the <legacyBold>Supports</legacyBold> method should test for.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="ffc6e245-4471-42ae-84dd-e85bddfce983">CursorTypeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the type of cursor used in a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the data type of a <legacyBold>Field</legacyBold>, <legacyBold>Parameter</legacyBold>, or <legacyBold>Property</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="45d54b6e-db2c-4553-9fd0-528147d6da2f">EditModeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the editing status of a record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea">ErrorValueEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the type of ADO run-time error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="7d4a5496-ec2d-4936-b36a-7049a82be4b4">EventReasonEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the reason that caused an event to occur.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the current status of the execution of an event.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies how a provider should execute a command.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2">FieldEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the special fields referenced in the <legacyBold>Fields</legacyBold> collection of a <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="6e34d886-005a-40dc-bd5c-6adcbf81e5cd">FieldAttributeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies one or more attributes of a <legacyBold>Field</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="e06da1e2-303f-41b2-a3b0-61e233da152c">FieldStatusEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the status of a <legacyBold>Field</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="b22e725e-84bd-4286-a070-290c278c3783">FilterGroupEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the group of records to be filtered from a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="adc109b9-79f4-4946-a5eb-658e22e9a8a5">GetRowsOptionEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies how many records to retrieve from a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf">IsolationLevelEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the level of transaction isolation for a <legacyBold>Connection</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="0440b793-99c7-49a2-b3e2-ec5b1a7e3e60">LineSeparatorsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the character used as a line separator in text <legacyBold>Stream</legacyBold> objects.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="d2894eaf-4450-4ace-aa51-c8b875fd3010">LockTypeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the type of lock placed on records during editing.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="4013075d-dbea-4bbc-a6f4-c345a55c5633">MarshalOptionsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies which records should be returned to the server.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="f53c2ce4-1021-4a45-92b8-775e8bebad99">MoveRecordOptionsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the behavior of the <legacyBold>Record</legacyBold> object <legacyBold>MoveRecord</legacyBold> method.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="32746558-097b-4749-989e-519aadf7e3f4">ObjectStateEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether an object is open or closed, connecting to a data source, executing a command, or fetching data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="7ef6c728-5eda-4bde-8052-02d2db1d2cfe">ParameterAttributesEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the attributes of a <legacyBold>Parameter</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3">ParameterDirectionEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether the <legacyBold>Parameter</legacyBold> represents an input parameter, an output parameter, or both, or if the parameter is the return value from a stored procedure.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="ebe1a2ab-e9f1-43a2-8f94-b190c9613d70">PersistFormatEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the format in which to save a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="e69af0a5-3405-4b72-9c6e-6b188ff746fd">PositionEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the current position of the record pointer within a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="96a01955-a6b4-4cbf-9c73-52bcd1e9fb25">PropertyAttributesEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the attributes of a <legacyBold>Property</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="6d746670-0850-4065-9cd4-168dea1d3ea9">RecordCreateOptionsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies for the <legacyBold>Record</legacyBold> object <legacyBold>Open</legacyBold> method whether an existing <legacyBold>Record</legacyBold> should be opened, or a new <legacyBold>Record</legacyBold> should be created. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="9028aba4-90fc-4dfc-88e4-fa8a7b6fedee">RecordOpenOptionsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies options for opening a <legacyBold>Record</legacyBold>. These values may be combined by using an OR operator.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="506fdd70-4452-4e83-95d5-c94311988dfa">RecordStatusEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the status of a record with regard to batch updates and other bulk operations.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="f557e537-015d-4ba7-8a41-a6f00b366a91">RecordTypeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the type of <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="d3df2c90-e570-4c40-a79a-25b3448a009c">ResyncEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether underlying values are overwritten by a call to <legacyBold>Resync</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="59339100-6e29-48d1-aea3-6873796d186b">SaveOptionsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether a file should be created or overwritten when saving from a <legacyBold>Stream</legacyBold> object. The values can be combined with an AND operator.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="21c97651-297f-469f-b5b5-c48af72b62a8">SchemaEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the type of schema <legacyBold>Recordset</legacyBold> that the <legacyBold>OpenSchema</legacyBold> method retrieves. Specifies the direction of a record search within a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="81272ae3-2165-4f4e-adfe-9ede0368cb17">SearchDirectionEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the direction of a record search within a <legacyBold>Recordset</legacyBold>. Specifies the type of <legacyBold>Seek</legacyBold> to execute.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="f0ec0c92-8253-47c6-9a14-e5dbccbad219">SeekEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the type of <legacyBold>Seek</legacyBold> to execute. Specifies options for opening a <legacyBold>Stream</legacyBold> object. The values can be combined with an AND operator.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="85b6c57f-47ed-46ba-bd92-07882ae9e9d2">StreamOpenOptionsEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies options for opening a <legacyBold>Stream</legacyBold> object. The values can be combined with an AND operator. Specifies whether the whole stream or the next line should be read from a <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="cfa1b416-003a-436f-a21b-bd2397e54db3">StreamReadEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether the whole stream or the next line should be read from a <legacyBold>Stream</legacyBold> object. Specifies the type of data stored in a <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="220fe51d-4889-4020-a099-2ec9c7485503">StreamTypeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the type of data stored in a <legacyBold>Stream</legacyBold> object. Specifies whether a line separator is appended to the string written to a <legacyBold>Stream</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7">StreamWriteEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies whether a line separator is appended to the string written to a <legacyBold>Stream</legacyBold> object. Specifies the format when retrieving a <legacyBold>Recordset</legacyBold> as a string.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="28f7d1ec-092b-4323-a39d-d3f882c6c81a">StringFormatEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the format when retrieving a <legacyBold>Recordset</legacyBold> as a string. Specifies the transaction attributes of a <legacyBold>Connection</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="e7dcecd3-7dc7-445c-b922-f700c3067fbc">XactAttributeEnum</legacyLink>             </para>
          </TD>
          <TD>
            <para>Specifies the transaction attributes of a <legacyBold>Connection</legacyBold> object.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="bfd96a4b-c913-45aa-9e4c-ec86ac364f3a">ADO API Reference</link>
<link xlink:href="b5e1d26d-b41d-4e35-8c7c-972426473dfb">ADO Collections</link>
<link xlink:href="d7b06d72-f792-4328-93a2-5006b9e2c581">ADO Dynamic Properties</link>
<link xlink:href="0ce201c3-6657-4c87-ae81-0d7dc5b5a431">ADO Errors</link>
<link xlink:href="0ded5ad9-8f83-4224-95af-38512783b972">ADO Events</link>
<link xlink:href="a38c5670-ba28-44f3-bd5b-fcb46880e904">ADO Methods</link>
<link xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</link>
<link xlink:href="d0b7e254-c89f-4406-b846-a060ef038c30">ADO Objects</link>
<link xlink:href="0ac0d1a7-6c7a-4f4c-b115-428935e0f98b">ADO Properties</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>