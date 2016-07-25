---
title: "The Field Object"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d1c4ad5-4be3-42ab-b516-e7133ca300bc
caps.latest.revision: 10
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
# The Field Object
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each <legacyBold>Field</legacyBold> object usually corresponds to a column in a database table. However, a <legacyBold>Field</legacyBold> can also represent a pointer to another <legacyBold>Recordset</legacyBold>, called a chapter. Exceptions, such as chapter columns, will be covered later in this guide.</para>
    <para>Use the <legacyBold>Value</legacyBold> property of <legacyBold>Field</legacyBold> objects to set or return data for the current record. Depending on the functionality the provider exposes, some collections, methods, or properties of a <legacyBold>Field</legacyBold> object may not be available.</para>
    <para>With the collections, methods, and properties of a <legacyBold>Field</legacyBold> object, you can do the following:   </para>
    <list class="bullet">
      <listItem>
        <para>Return the name of a field by using the <legacyBold>Name</legacyBold> property.</para>
      </listItem>
      <listItem>
        <para>View or change the data in the field by using the <legacyBold>Value</legacyBold> property. <legacyBold>Value </legacyBold>is the default property of the <legacyBold>Field</legacyBold> object.</para>
      </listItem>
      <listItem>
        <para>Return the basic characteristics of a field by using the <legacyBold>Type</legacyBold>, <legacyBold>Precision</legacyBold>, and <legacyBold>NumericScale</legacyBold> properties.</para>
      </listItem>
      <listItem>
        <para>Return the declared size of a field by using the <legacyBold>DefinedSize</legacyBold> property.</para>
      </listItem>
      <listItem>
        <para>Return the actual size of the data in a given field by using the <legacyBold>ActualSize</legacyBold> property.</para>
      </listItem>
      <listItem>
        <para>Determine what types of functionality are supported for a given field by using the <legacyBold>Attributes</legacyBold> property and <legacyBold>Properties</legacyBold> collection.</para>
      </listItem>
      <listItem>
        <para>Manipulate the values of fields containing long binary or long character data by using the <legacyBold>AppendChunk</legacyBold> and <legacyBold>GetChunk</legacyBold> methods.</para>
      </listItem>
    </list>
    <para>Resolve discrepancies in field values during batch updating by using the <legacyBold>OriginalValue</legacyBold> and <legacyBold>UnderlyingValue</legacyBold> properties, if the provider supports batch updates. </para>
  </introduction>
  <section>
    <title>Describing a Field</title>
    <content>
      <para>The topics that follow will discuss properties of the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object that represent information that describes the <legacyBold>Field</legacyBold> object itself — that is, metadata about the field. This information can be used to determine much about the schema of the <legacyBold>Recordset</legacyBold>. These properties include <legacyBold>Type</legacyBold>, <legacyBold>DefinedSize</legacyBold> and <legacyBold>ActualSize</legacyBold>, <legacyBold>Name</legacyBold>, and <legacyBold>NumericScale</legacyBold> and <legacyBold>Precision</legacyBold>.</para>
    </content>
    <sections>
      <section>
        <title>Discovering the Data Type</title>
        <content>
          <para>The <legacyBold>Type</legacyBold> property indicates the data type of the field. The data type enumerated constants that are supported by ADO are described in <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink> in the <legacyItalic>ADO Programmer's Reference</legacyItalic>.</para>
          <para>For floating point numeric types such <legacyBold>adNumeric</legacyBold>, you can obtain more information. The <legacyBold>NumericScale</legacyBold> property indicates how many digits to the right of the decimal point will be used to represent values for the <legacyBold>Field</legacyBold>. The <legacyBold>Precision</legacyBold> property specifies the maximum number of digits used to represent values for the <legacyBold>Field</legacyBold>.</para>
        </content>
      </section>
      <section>
        <title>Determining Field Size</title>
        <content>
          <para>Use the <legacyBold>DefinedSize</legacyBold> property to determine the data capacity of a <legacyBold>Field</legacyBold> object.</para>
          <para>Use the <legacyBold>ActualSize</legacyBold> property to return the actual length of a <legacyBold>Field</legacyBold> object's value. For all fields, the <legacyBold>ActualSize</legacyBold> property is read-only. If ADO cannot determine the length of the <legacyBold>Field</legacyBold> object's value, the <legacyBold>ActualSize</legacyBold> property returns <legacyBold>adUnknown</legacyBold>.</para>
          <para>The <legacyBold>DefinedSize</legacyBold> and <legacyBold>ActualSize</legacyBold> properties have different purposes. For example, consider a <legacyBold>Field</legacyBold> object with a declared type of <legacyBold>adVarChar</legacyBold> and a <legacyBold>DefinedSize</legacyBold> property value of 50, containing a single character. The <legacyBold>ActualSize</legacyBold> property value it returns is the length in bytes of the single character.</para>
        </content>
      </section>
      <section>
        <title>Determining Field Contents</title>
        <content>
          <para>The identifier of the column from the data source is represented by the <legacyBold>Name</legacyBold> property of the <legacyBold>Field</legacyBold>. The <legacyBold>Value</legacyBold> property of the <legacyBold>Field</legacyBold> object returns or sets the actual data content of the field. This is the default property.</para>
          <para>To change the data in a field, set the <legacyBold>Value</legacyBold> property equal to a new value of the correct type. Your cursor type must support updates to change the contents of a field. Database validation is not done here in batch mode, so you will need to check for errors when you call <legacyBold>UpdateBatch</legacyBold> in such a case. Some providers also support the ADO <legacyBold>Field</legacyBold> object's <legacyBold>UnderlyingValue</legacyBold> and <legacyBold>OriginalValue</legacyBold> properties to assist you with resolving conflicts when you attempt to perform batch updates. For details about how to resolve such conflicts, see <legacyLink xlink:href="ef514f85-c446-4f05-824e-c9313b2ffae1">Editing Data</legacyLink>.</para>
          <alert class="note">
            <para>               <legacyBold>Recordset Field</legacyBold> values cannot be set when appending new <legacyBold>Fields</legacyBold> to a <legacyBold>Recordset</legacyBold>. Rather, new <legacyBold>Fields</legacyBold> can be appended to a closed <legacyBold>Recordset</legacyBold>. Then the <legacyBold>Recordset</legacyBold> must be opened, and only then can values be assigned to these <legacyBold>Fields</legacyBold>.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Getting More Field Information</title>
        <content>
          <para>ADO objects have two types of properties: built-in and dynamic. To this point, only the built-in properties of the <legacyBold>Field</legacyBold> object have been discussed.</para>
          <para>Built-in properties are those properties implemented in ADO and immediately available to any new object, using the <codeInline>MyObject.Property</codeInline> syntax. They do not appear as <legacyBold>Property</legacyBold> objects in an object's <legacyBold>Properties</legacyBold> collection.</para>
          <para>Dynamic properties are defined by the underlying data provider, and appear in the <legacyBold>Properties</legacyBold> collection for the appropriate ADO object. For example, a property specific to the provider may indicate if a <legacyBold>Recordset</legacyBold> object supports transactions or updating. These additional properties will appear as <legacyBold>Property</legacyBold> objects in that <legacyBold>Recordset</legacyBold> object's <legacyBold>Properties</legacyBold> collection. Dynamic properties can be referenced only through the collection, using the syntax <codeInline>MyObject.Properties(0)</codeInline> or <codeInline>MyObject.Properties("Name")</codeInline>.</para>
          <para>You cannot delete either kind of property.</para>
          <para>A dynamic <legacyBold>Property</legacyBold> object has four built-in properties of its own:   </para>
          <list class="bullet">
            <listItem>
              <para>The <legacyBold>Name</legacyBold> property is a string that identifies the property.</para>
            </listItem>
            <listItem>
              <para>The <legacyBold>Type</legacyBold> property is an integer that specifies the property data type.</para>
            </listItem>
            <listItem>
              <para>The <legacyBold>Value</legacyBold> property is a variant that contains the property setting. <legacyBold>Value</legacyBold> is the default property for a <legacyBold>Property</legacyBold> object.</para>
            </listItem>
            <listItem>
              <para>The <legacyBold>Attributes</legacyBold> property is a <legacyBold>Long</legacyBold> value that indicates characteristics of the property specific to the provider.</para>
            </listItem>
          </list>
          <para>The <legacyBold>Properties</legacyBold> collection for the <legacyBold>Field</legacyBold> object contains additional metadata about the field. The contents of this collection vary depending upon the provider. The following code example examines the <legacyBold>Properties</legacyBold> collection of the sample <legacyBold>Recordset</legacyBold> introduced at the beginning of this section. It first looks at the contents of the collection. This code uses the <legacyLink xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">OLE DB Provider for SQL Server</legacyLink>, so the <legacyBold>Properties</legacyBold> collection contains information relevant to that provider.</para>
          <code>'BeginFieldProps
    Dim objProp As ADODB.Property
        
    For intLoop = 0 To (objFields.Count - 1)
        Debug.Print objFields.Item(intLoop).Name
        
        For Each objProp In objFields(intLoop).Properties
            Debug.Print vbTab &amp; objProp.Name &amp; " = " &amp; objProp.Value
        Next objProp
    Next intLoop
'EndFieldProps</code>
        </content>
      </section>
      <section>
        <title>Dealing with Binary Data</title>
        <content>
          <para>Use the <legacyLink xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk</legacyLink> method on a <legacyBold>Field</legacyBold> object to fill it with long binary or character data. In situations where system memory is limited, you can use the <legacyBold>AppendChunk</legacyBold> method to manipulate long values in portions rather than in their entirety.</para>
          <para>If the <legacyBold>adFldLong</legacyBold> bit in the <legacyBold>Attributes</legacyBold> property of a <legacyBold>Field</legacyBold> object is set to <legacyBold>True</legacyBold>, you can use the <legacyBold>AppendChunk</legacyBold> method for that field.</para>
          <para>The first <legacyBold>AppendChunk</legacyBold> call on a <legacyBold>Field</legacyBold> object writes data to the field, overwriting any existing data. Subsequent <legacyBold>AppendChunk</legacyBold> calls add to existing data. If you are appending data to one field and then you set or read the value of another field in the current record, ADO assumes that you are finished appending data to the first field. If you call the <legacyBold>AppendChunk</legacyBold> method on the first field again, ADO interprets the call as a new <legacyBold>AppendChunk</legacyBold> operation and overwrites the existing data. Accessing fields in other <legacyBold>Recordset</legacyBold> objects that are not clones of the first <legacyBold>Recordset</legacyBold> object will not disrupt <legacyBold>AppendChunk</legacyBold> operations.</para>
          <para>Use the <legacyBold>GetChunk</legacyBold> method on a <legacyBold>Field</legacyBold> object to retrieve part or all of its long binary or character data. In situations where system memory is limited, you can use the <legacyBold>GetChunk</legacyBold> method to manipulate long values in portions, rather than in their entirety.</para>
          <para>The data that a <legacyBold>GetChunk</legacyBold> call returns is assigned to <legacyItalic>variable</legacyItalic>. If <legacyItalic>Size</legacyItalic> is greater than the remaining data, the <legacyBold>GetChunk</legacyBold> method returns only the remaining data without padding <legacyItalic>variable</legacyItalic> with empty spaces. If the field is empty, the <legacyBold>GetChunk</legacyBold> method returns a null value.</para>
          <para>Each subsequent <legacyBold>GetChunk</legacyBold> call retrieves data starting from where the previous <legacyBold>GetChunk</legacyBold> call left off. However, if you are retrieving data from one field and then set or read the value of another field in the current record, ADO assumes you have finished retrieving data from the first field. If you call the <legacyBold>GetChunk</legacyBold> method on the first field again, ADO interprets the call as a new <legacyBold>GetChunk</legacyBold> operation and starts reading from the beginning of the data. Accessing fields in other <legacyBold>Recordset</legacyBold> objects that are not clones of the first <legacyBold>Recordset</legacyBold> object will not disrupt <legacyBold>GetChunk</legacyBold> operations.</para>
          <para>If the <legacyBold>adFldLong</legacyBold> bit in the <legacyBold>Attributes</legacyBold> property of a <legacyBold>Field</legacyBold> object is set to <legacyBold>True</legacyBold>, you can use the <legacyBold>GetChunk</legacyBold> method for that field.</para>
          <para>If there is no current record when you use the <legacyBold>GetChunk</legacyBold> or <legacyBold>AppendChunk</legacyBold> method on a <legacyBold>Field</legacyBold> object, error 3021 (no current record) occurs.</para>
          <para>For an example of using these methods to manipulate binary data, see the <legacyLink xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk Method</legacyLink> and <legacyLink xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk Method</legacyLink> examples in the <legacyItalic>ADO Programmer's Reference</legacyItalic>.</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>