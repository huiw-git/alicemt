---
title: "Append Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
caps.latest.revision: 17
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
# Append Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Appends an object to a collection. If the collection is <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink>, a new <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object can be created before it is appended to the collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
collection.Append object
fields.Append Name, Type, DefinedSize, Attrib, FieldValue</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>collection</legacyItalic> </definedTerm>
        <definition>
          <para>A collection object.</para>
        </definition>
        <definedTerm> <legacyItalic>fields</legacyItalic> </definedTerm>
        <definition>
          <para>A <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection.</para>
        </definition>
        <definedTerm> <legacyItalic>object</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents the object to be appended.</para>
        </definition>
        <definedTerm> <legacyItalic>Name</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains the name of the new <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> object, and must not be the same name as any other object in <legacyItalic>fields</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>Type</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink> value, whose default value is <legacyBold>adEmpty</legacyBold>, that specifies the data type of the new field. The following data types are not supported by ADO, and should not be used when appending new fields to a <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object (ADO)</link>: <legacyBold>adIDispatch</legacyBold>, <legacyBold>adIUnknown</legacyBold>, <legacyBold>adVariant</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>DefinedSize</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Long</languageKeyword> value that represents the defined size, in characters or bytes, of the new field. The default value for this parameter is derived from <parameterReference>Type</parameterReference>. Fields that have a <parameterReference>DefinedSize</parameterReference> greater than 255 bytes are treated as variable length columns. The default for <parameterReference>DefinedSize</parameterReference> is unspecified.</para>
        </definition>
        <definedTerm> <legacyItalic>Attrib</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="6e34d886-005a-40dc-bd5c-6adcbf81e5cd">FieldAttributeEnum</legacyLink> value, whose default value is <legacyBold>adFldDefault</legacyBold>, that specifies attributes for the new field. If this value is not specified, the field will contain attributes derived from <parameterReference>Type</parameterReference>.</para>
        </definition>
        <definedTerm> <legacyItalic>FieldValue</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> that represents the value for the new field. If not specified, the field is appended with a null value.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content />
    <sections>
      <section>
        <title>Parameters Collection</title>
        <content>
          <para>You must set the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property of a <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object before appending it to the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection. If you select a variable-length data type, you must also set the <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink> property to a value greater than zero.</para>
          <para>Describing parameters yourself minimizes calls to the provider and therefore improves performance when you use stored procedures or parameterized queries. However, you must know the properties of the parameters associated with the stored procedure or parameterized query that you want to call. </para>
          <para>Use the <legacyLink xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter</legacyLink> method to create <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> objects with the appropriate property settings and use the <unmanagedCodeEntityReference>Append</unmanagedCodeEntityReference> method to add them to the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection. This lets you set and return parameter values without having to call the provider for the parameter information. If you are writing to a provider that does not supply parameter information, you must use this method to manually populate the <unmanagedCodeEntityReference>Parameters</unmanagedCodeEntityReference> collection in order to use parameters at all.</para>
        </content>
      </section>
      <section>
        <title>Fields Collection</title>
        <content>
          <para>The <legacyItalic>FieldValue</legacyItalic> parameter is only valid when adding a <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> object to a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object, not to a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object. With a <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object, you can append fields and provide values at the same time. With a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object, you must create fields while the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is closed, and then open the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> and assign values to the fields.</para>
          <alert class="note">
            <para>For new <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> objects that have been appended to the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection of a <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object, the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property must be set before any other <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> properties can be specified. First, a specific value for the <unmanagedCodeEntityReference>Value</unmanagedCodeEntityReference> property must have been assigned and <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> on the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection called. Then, other properties such as <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> or <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> can be accessed. <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> objects of the following data types (<legacyBold>DataTypeEnum</legacyBold>) cannot be appended to the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection and will cause an error to occur: <legacyBold>adArray</legacyBold>, <legacyBold>adChapter</legacyBold>, <legacyBold>adEmpty</legacyBold>, <legacyBold>adPropVariant</legacyBold>, and <legacyBold>adUserDefined</legacyBold>. Also, the following data types are not supported by ADO: <legacyBold>adIDispatch</legacyBold>, <legacyBold>adIUnknown</legacyBold>, and <legacyBold>adIVariant</legacyBold>. For these types, no error will occur when appended, but usage can produce unpredictable results including memory leaks.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Recordset</title>
        <content>
          <para>If you do not set the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property before calling the <unmanagedCodeEntityReference>Append</unmanagedCodeEntityReference> method, <unmanagedCodeEntityReference>CursorLocation</unmanagedCodeEntityReference> will be set to <legacyBold>adUseClient</legacyBold> (a <legacyLink xlink:href="acb255ff-1734-4b70-89bb-aef862b4c63b">CursorLocationEnum</legacyLink> value) automatically when the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object is called.</para>
          <para>A run-time error will occur if the <unmanagedCodeEntityReference>Append </unmanagedCodeEntityReference>method is called on the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection of an open <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>, or on a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> where the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property has been set. You can only append fields to a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> that is not open and has not yet been connected to a data source. This is typically the case when a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object is fabricated with the <legacyLink xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset</legacyLink> method or assigned to an object variable.</para>
        </content>
      </section>
      <section>
        <title>Record</title>
        <content>
          <para>A run-time error will not occur if the <unmanagedCodeEntityReference>Append</unmanagedCodeEntityReference> method is called on the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection of an open <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference>. The new field will be added to the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection of the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object. If the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> was derived from a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>, the new field will not appear in the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection of the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object.</para>
          <para>A non-existent field can be created and appended to the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection by assigning a value to the field object as if it already existed in the collection. The assignment will trigger the automatic creation and appending of the <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> object, and then the assignment will be completed.</para>
          <para>After appending a <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> to the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection of a <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object, call the <unmanagedCodeEntityReference>Update</unmanagedCodeEntityReference> method of the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection to save the change.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="46908cbd-434f-43e7-a794-ed0be0e0c0a7">Visual Basic Example</link>
<link xlink:href="b57d144c-0a34-49c8-94cf-e5981edfcca6">Visual C++ Example</link>
<link xlink:href="9673f232-fa58-4439-995a-b4066db628aa">Visual J++ Example</link>
<link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
<link xlink:href="25bedc25-c51c-4cab-96ce-930b959965d9">Delete Method (ADO Fields Collection)</link>
<link xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete Method (ADO Parameters Collection)</link>
<link xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete Method (ADO Recordset)</link>
<link xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>