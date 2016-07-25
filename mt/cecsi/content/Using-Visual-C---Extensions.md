---
title: "Using Visual C++ Extensions"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff759185-df41-4507-8d12-0921894ffbd9
caps.latest.revision: 14
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
# Using Visual C++ Extensions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>The IADORecordBinding Interface</title>
    <content>
      <para>The Microsoft Visual C++ Extensions for ADO associate, or bind, fields of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object to C/C++ variables. Whenever the current row of the bound <legacyBold>Recordset</legacyBold> changes, all the bound fields in the <legacyBold>Recordset</legacyBold> are copied to the C/C++ variables. If necessary, the copied data is converted to the declared data type of the C/C++ variable.</para>
      <para>The <legacyBold>BindToRecordset</legacyBold> method of the <legacyBold>IADORecordBinding</legacyBold> interface binds fields to C/C++ variables. The <legacyBold>AddNew</legacyBold> method adds a new row to the bound <legacyBold>Recordset</legacyBold>. The <legacyBold>Update</legacyBold> method populates fields in new rows of the <legacyBold>Recordset</legacyBold>, or updates fields in existing rows, with the value of the C/C++ variables.</para>
      <para>The <legacyBold>IADORecordBinding</legacyBold> interface is implemented by the <legacyBold>Recordset</legacyBold> object. You do not code the implementation yourself.</para>
    </content>
  </section>
  <section>
    <title>Binding Entries</title>
    <content>
      <para>The Visual C++ Extensions for ADO map fields of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object to C/C++ variables. The definition of a mapping between a field and a variable is called a <legacyItalic>binding entry</legacyItalic>. Macros provide binding entries for numeric, fixed-length, and variable-length data. The binding entries and C/C++ variables are declared in a class derived from the Visual C++ Extensions class, <legacyBold>CADORecordBinding</legacyBold>. The <legacyBold>CADORecordBinding</legacyBold> class is defined internally by the binding entry macros.</para>
      <para>ADO internally maps the parameters in these macros to an OLE DB <legacyBold>DBBINDING</legacyBold> structure and creates an OLE DB <legacyBold>Accessor</legacyBold> object to manage the movement and conversion of data between fields and variables. OLE DB defines data as consisting of three parts: A <legacyItalic>buffer</legacyItalic> where the data is stored; a <legacyItalic>status</legacyItalic> that indicates whether a field was successfully stored in the buffer, or how the variable should be restored to the field; and the <legacyItalic>length</legacyItalic> of the data. (See <legacyLink xlink:href="4369708b-c9fb-4d48-a321-bf949b41a369">Getting and Setting Data (OLE DB)</legacyLink>in the OLE DB Programmer's Reference, for more information.)</para>
    </content>
  </section>
  <section>
    <title>Header File</title>
    <content>
      <para>Include the following file in your application in order to use the Visual C++ Extensions for ADO:</para>
      <code>#include &lt;icrsint.h&gt;</code>
    </content>
  </section>
  <section>
    <title>Binding Recordset Fields</title>
    <content>
      <procedure>
        <title>To Bind Recordset Fields to C/C++ Variables</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Create a class derived from the <legacyBold>CADORecordBinding</legacyBold> class.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Specify binding entries and corresponding C/C++ variables in the derived class. Bracket the binding entries between <legacyBold>BEGIN_ADO_BINDING</legacyBold> and <legacyBold>END_ADO_BINDING</legacyBold> macros. Do not terminate the macros with commas or semicolons. Appropriate delimiters are specified automatically by each macro. </para>
              <para>Specify one binding entry for each field to be mapped to a C/C++ variable. Use an appropriate member from the <legacyBold>ADO_FIXED_LENGTH_ENTRY</legacyBold>, <legacyBold>ADO_NUMERIC_ENTRY</legacyBold>, or <legacyBold>ADO_VARIABLE_LENGTH_ENTRY</legacyBold> family of macros. </para>
            </content>
          </step>
          <step>
            <content>
              <para>In your application, create an instance of the class derived from <legacyBold>CADORecordBinding</legacyBold>. Get the <legacyBold>IADORecordBinding</legacyBold> interface from the <legacyBold>Recordset</legacyBold>. Then call the <legacyBold>BindToRecordset</legacyBold> method to bind the <legacyBold>Recordset</legacyBold> fields to the C/C++ variables.</para>
            </content>
          </step>
        </steps>
      </procedure>
      <para>For more information, see the <legacyLink xlink:href="9739c278-582c-402b-a158-7f68a1b2c293">Visual C++ Extensions Example</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Interface Methods</title>
    <content>
      <para>The <legacyBold>IADORecordBinding</legacyBold> interface has three methods: <legacyBold>BindToRecordset</legacyBold>, <legacyBold>AddNew</legacyBold>, and <legacyBold>Update</legacyBold>. The sole argument to each method is a pointer to an instance of the class derived from <legacyBold>CADORecordBinding</legacyBold>. Therefore, the <legacyBold>AddNew</legacyBold> and <legacyBold>Update</legacyBold> methods cannot specify any of the parameters of their ADO method namesakes.</para>
    </content>
  </section>
  <section>
    <title>Syntax</title>
    <content>
      <para>The <legacyBold>BindToRecordset</legacyBold> method associates the <legacyBold>Recordset</legacyBold> fields with C/C++ variables.</para>
      <code>BindToRecordset(CADORecordBinding <legacyItalic>*binding</legacyItalic>)</code>
      <para>The <legacyBold>AddNew</legacyBold> method invokes its namesake, the ADO <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method, to add a new row to the <legacyBold>Recordset</legacyBold>.</para>
      <code>AddNew(CADORecordBinding <legacyItalic>*binding</legacyItalic>)</code>
      <para>The <legacyBold>Update</legacyBold> method invokes its namesake, the ADO <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method, to update the <legacyBold>Recordset</legacyBold>.</para>
      <code>Update(CADORecordBinding <legacyItalic>*binding</legacyItalic>)</code>
    </content>
  </section>
  <section>
    <title>Binding Entry Macros</title>
    <content>
      <para>Binding entry macros define the association of a <legacyBold>Recordset</legacyBold> field and a variable. A beginning and ending macro delimits the set of binding entries.</para>
      <para>Families of macros are provided for fixed-length data, such as <legacyBold>adDate</legacyBold> or <legacyBold>adBoolean</legacyBold>; numeric data, such as <legacyBold>adTinyInt</legacyBold>, <legacyBold>adInteger</legacyBold>, or <legacyBold>adDouble</legacyBold>; and variable-length data, such as <legacyBold>adChar</legacyBold>, <legacyBold>adVarChar</legacyBold> or <legacyBold>adVarBinary</legacyBold>. All numeric types, except for <legacyBold>adVarNumeric</legacyBold>, are also fixed-length types. Each family has differing sets of parameters so that you can exclude binding information that is of no interest.</para>
      <para>For more information, see <legacyLink xlink:href="e3a0533a-2196-4eb0-a31e-92fe9556ada6">Appendix A: Data Types</legacyLink>, of the OLE DB Programmer's Reference.</para>
    </content>
    <sections>
      <section>
        <title>Begin Binding Entries</title>
        <content>
          <para>
            <legacyBold>BEGIN_ADO_BINDING</legacyBold>(<legacyItalic>Class</legacyItalic>)</para>
        </content>
      </section>
      <section>
        <title>Fixed-Length Data</title>
        <content>
          <para>
            <legacyBold>ADO_FIXED_LENGTH_ENTRY</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Status, Modify</legacyItalic>)</para>
          <para>
            <legacyBold>ADO_FIXED_LENGTH_ENTRY2</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Modify</legacyItalic>)</para>
        </content>
      </section>
      <section>
        <title>Numeric Data</title>
        <content>
          <para>
            <legacyBold>ADO_NUMERIC_ENTRY</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Precision, Scale, Status, Modify</legacyItalic>)</para>
          <para>
            <legacyBold>ADO_NUMERIC_ENTRY2</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Precision, Scale, Modify</legacyItalic>)</para>
        </content>
      </section>
      <section>
        <title>Variable-Length Data</title>
        <content>
          <para>
            <legacyBold>ADO_VARIABLE_LENGTH_ENTRY</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Size, Status, Length, Modify</legacyItalic>)</para>
          <para>
            <legacyBold>ADO_VARIABLE_LENGTH_ENTRY2</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Size, Status, Modify</legacyItalic>)</para>
          <para>
            <legacyBold>ADO_VARIABLE_LENGTH_ENTRY3</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Size, Length, Modify</legacyItalic>)</para>
          <para>
            <legacyBold>ADO_VARIABLE_LENGTH_ENTRY4</legacyBold>(<legacyItalic>Ordinal, DataType, Buffer, Size, Modify</legacyItalic>)</para>
        </content>
      </section>
      <section>
        <title>End Binding Entries</title>
        <content>
          <para>
            <legacyBold>END_ADO_BINDING</legacyBold>()</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Parameter</para>
                </TD>
                <TD>
                  <para>Description</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Class</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Class in which the binding entries and C/C++ variables are defined. </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Ordinal</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Ordinal number, counting from one, of the <legacyBold>Recordset</legacyBold> field corresponding to your C/C++ variable.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>DataType</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Equivalent ADO data type of the C/C++ variable (see <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink> for a list of valid data types). The value of the <legacyBold>Recordset</legacyBold> field will be converted to this data type if necessary.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Buffer</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Name of the C/C++ variable where the <legacyBold>Recordset</legacyBold> field will be stored.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Size</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Maximum size in bytes of <legacyItalic>Buffer</legacyItalic>. If <legacyItalic>Buffer </legacyItalic>will contain a variable-length string, allow room for a terminating zero.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Status</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Name of a variable that will indicate whether the contents of <legacyItalic>Buffer </legacyItalic>are valid, and whether the conversion of the field to <legacyItalic>DataType </legacyItalic>was successful.</para>
                  <para>The two most important values for this variable are <legacyBold>adFldOK</legacyBold>, which means the conversion was successful; and <legacyBold>adFldNull</legacyBold>, which means the value of the field would be a VARIANT of type VT_NULL and not merely empty.</para>
                  <para>Possible values for <legacyItalic>Status </legacyItalic>are listed in the next table, "Status Values."</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Modify</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Boolean flag; if TRUE, indicates ADO is allowed to update the corresponding <legacyBold>Recordset</legacyBold> field with the value contained in <legacyItalic>Buffer</legacyItalic>.</para>
                  <para>Set the Boolean <legacyItalic>modify</legacyItalic> parameter to TRUE to enable ADO to update the bound field, and FALSE if you want to examine the field but not change it.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Precision</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Number of digits that can be represented in a numeric variable.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Scale</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Number of decimal places in a numeric variable.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Length</legacyItalic>
                  </para>
                </TD>
                <TD>
                  <para>Name of a four-byte variable that will contain the actual length of the data in <legacyItalic>Buffer</legacyItalic>.</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Status Values</title>
    <content>
      <para>The value of the <legacyItalic>Status</legacyItalic> variable indicates whether a field was successfully copied to a variable.</para>
      <para>When setting data, <legacyItalic>Status </legacyItalic>may be set to <legacyBold>adFldNull</legacyBold> to indicate the <legacyBold>Recordset</legacyBold> field should be set to null.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
            <TD>
              <para>Value</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldOK</legacyBold>
              </para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>A non-null field value was returned.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldBadAccessor</legacyBold>
              </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Binding was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldCantConvertValue</legacyBold>
              </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Value couldn't be converted for reasons other than sign mismatch or data overflow.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldNull</legacyBold>
              </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>When getting a field, indicates a null value was returned.</para>
              <para>When setting a field, indicates the field should be set to <legacyBold>NULL</legacyBold> when the field cannot encode <legacyBold>NULL</legacyBold> itself (for example, a character array or an integer).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldTruncated</legacyBold>
              </para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>Variable-length data or numeric digits were truncated.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldSignMismatch</legacyBold>
              </para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para>Value is signed and variable data type is unsigned.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldDataOverFlow</legacyBold>
              </para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para>Value is larger than could be stored in the variable data type.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldCantCreate</legacyBold>
              </para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para>Unknown column type and field already open.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldUnavailable</legacyBold>
              </para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>Field value could not be determined—for example, on a new, unassigned field with no default value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldPermissionDenied</legacyBold>
              </para>
            </TD>
            <TD>
              <para>9</para>
            </TD>
            <TD>
              <para>When updating, no permission to write data.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldIntegrityViolation</legacyBold>
              </para>
            </TD>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>When updating, field value would violate column integrity.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldSchemaViolation</legacyBold>
              </para>
            </TD>
            <TD>
              <para>11</para>
            </TD>
            <TD>
              <para>When updating, field value would violate column schema.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldBadStatus</legacyBold>
              </para>
            </TD>
            <TD>
              <para>12</para>
            </TD>
            <TD>
              <para>When updating, invalid status parameter.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adFldDefault</legacyBold>
              </para>
            </TD>
            <TD>
              <para>13</para>
            </TD>
            <TD>
              <para>When updating, a default value was used.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="9739c278-582c-402b-a158-7f68a1b2c293">ADO with Visual C++ Extensions Example</link>
<link xlink:href="e492d307-24cb-489c-a5b0-99cdc09b07da">Visual C++ Extensions Header</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>