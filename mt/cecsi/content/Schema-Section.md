---
title: "Schema Section"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ac6e524-2c92-48e8-b871-0a4b5c8fda18
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
# Schema Section
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The schema section is required. As the previous example shows, ADO writes out detailed metadata about each column to preserve the semantics of the data values as much as possible for updating. However, to load in the XML, ADO only requires the names of the columns and the rowset to which they belong. Here is an example of a minimal schema:</para>
    <code>&lt;xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"
    xmlns:rs="urn:schemas-microsoft-com:rowset"
    xmlns:z="#RowsetSchema"&gt;
  &lt;s:Schema id="RowsetSchema"&gt;
    &lt;s:ElementType name="row" content="eltOnly"&gt;
      &lt;s:AttributeType name="ShipperID"/&gt;
      &lt;s:AttributeType name="CompanyName"/&gt;
      &lt;s:AttributeType name="Phone"/&gt;
      &lt;s:Extends type="rs:rowbase"/&gt;
    &lt;/s:ElementType&gt;
  &lt;/s:Schema&gt;
  &lt;rs:data&gt;
...
  &lt;/rs:data&gt;
&lt;/xml&gt;</code>
    <para>In the previous example, ADO will treat the data as variable length strings because no type information is included in the schema.</para>
  </introduction>
  <section>
    <title>Creating Aliases for Column Names</title>
    <content>
      <para>The rs:name attribute allows you to create an alias for a column name so that a friendly name may appear in the column information exposed by the rowset and a shorter name may be used in the data section. For example, the previous schema could be modified to map ShipperID to s1, CompanyName to s2, and Phone to s3 as follows:</para>
      <code>&lt;s:Schema id="RowsetSchema"&gt; 
&lt;s:ElementType name="row" content="eltOnly" rs:updatable="true"&gt; 
&lt;s:AttributeType name="s1" rs:name="ShipperID" rs:number="1" ...&gt; 
...
&lt;/s:AttributeType&gt; 
&lt;s:AttributeType name="s2" rs:name="CompanyName" rs:number="2" ...&gt; 
...
&lt;/s:AttributeType&gt; 
&lt;s:AttributeType name="s3" rs:name="Phone" rs:number="3" ...&gt; 
...
&lt;/s:AttributeType&gt; 
...
&lt;/s:ElementType&gt; 
&lt;/s:Schema&gt;</code>
      <para>Then, in the data section, the row would use the name attribute (not rs:name) to refer to that column:</para>
      <code>"&lt;row s1="1" s2="Speedy Express" s3="(503) 555-9831"/&gt;</code>
      <para>Creating aliases for column names is required whenever a column name is not a valid attribute or tag name in XML. For example, "LastName" must have an alias because names with embedded spaces are invalid attributes. The following line will not be correctly handled by the XML parser, so you must create an alias to some other name that does not have an embedded space.</para>
      <code>&lt;row last name="Jones"/&gt;</code>
      <para>Whatever value you use for the name attribute must be used consistently in each place that the column is referenced in both the schema and data sections of the XML document. The following example shows the consistent use of s1:</para>
      <code>&lt;s:Schema id="RowsetSchema"&gt;
  &lt;s:ElementType name="row" content="eltOnly"&gt;
    &lt;s:attribute type="s1"/&gt;
    &lt;s:attribute type="CompanyName"/&gt;
    &lt;s:attribute type="s3"/&gt;
    &lt;s:extends type="rs:rowbase"/&gt;
  &lt;/s:ElementType&gt;
  &lt;s:AttributeType name="s1" rs:name="ShipperID" rs:number="1" 
    rs:maydefer="true" rs:writeunknown="true"&gt;
    &lt;s:datatype dt:type="i4" dt:maxLength="4" rs:precision="10" 
      rs:fixedlength="true" rs:maybenull="true"/&gt;
  &lt;/s:AttributeType&gt;
&lt;/s:Schema&gt;
&lt;rs:data&gt;
  &lt;z:row s1="1" CompanyName="Speedy Express" s3="(503) 555-9831"/&gt;
&lt;/rs:data&gt;</code>
      <para>Similarly, because there is no alias defined for<codeInline> CompanyName </codeInline>in the previous example,<codeInline> CompanyName </codeInline>must be used consistently throughout the document.</para>
    </content>
  </section>
  <section>
    <title>Data Types</title>
    <content>
      <para>You can apply a data type to a column with the dt:type attribute. For the definitive guide to allowed XML types, see the Data Types section of the <externalLink><linkText>W3C XML-Data specification</linkText><linkUri>http://www.w3.org/TR/1998/NOTE-XML-data/</linkUri></externalLink>. You can specify a data type in two ways: either specify the dt:type attribute directly on the column definition itself or use the s:datatype construct as a nested element of the column definition. For example,</para>
      <code>&lt;s:AttributeType name="Phone" &gt;
  &lt;s:datatype dt:type="string"/&gt;
&lt;/s:AttributeType&gt;</code>
      <para>is equivalent to</para>
      <code>&lt;s:AttributeType name="Phone" dt:type="string"/&gt;</code>
      <para>If you omit the dt:type attribute entirely from the row definition, by default, the column's type will be a variable length string.</para>
      <para>If you have more type information than simply the type name (for example, dt:maxLength), it makes it more readable to use the s:datatype child element. This is merely a convention, however, and not a requirement.</para>
      <para>The following examples show further how to include type information in your schema.</para>
      <code>&lt;!-- 1. String with no max length --&gt;
&lt;s:AttributeType name="title_id"/&gt;
&lt;!—or --&gt;
&lt;s:AttributeType name="title_id" dt:type="string"/&gt;

&lt;!—- 2. Fixed length string with max length of 6 --&gt;
&lt;s:AttributeType name="title_id"&gt;
    &lt;s:datatype dt:type="string" dt:maxLength="6" rs:fixedlength="true" /&gt;
&lt;/s:AttributeType&gt;

&lt;!—- 3. Variable length string with max length of 6 --&gt;
&lt;s:AttributeType name="title_id"&gt;
    &lt;s:datatype dt:type="string" dt:maxLength="6" /&gt;
&lt;/s:AttributeType&gt;

&lt;!—- 4. Integer --&gt;
&lt;s:AttributeType name="title_id" dt:type="int"/&gt;</code>
      <para>There is a subtle use of the rs:fixedlength attribute in the second example. A column with the rs:fixedlength attribute set to true means that the data must have the length defined in the schema. In this case, a valid value for title_id is "123456," as is "123   ." However, "123" would not be valid because its length is 3, not 6. See the OLE DB Programmer's Guide for a more complete description of the fixedlength property.</para>
    </content>
  </section>
  <section>
    <title>Handling Nulls</title>
    <content>
      <para>Null values are handled by the rs:maybenull attribute. If this attribute is set to true, the contents of the column can contain a null value. Furthermore, if the column is not found in a row of data, the user reading the data back from the rowset will get a null status from IRowset::GetData(). Consider the following column definitions from the Shippers table.</para>
      <code>&lt;s:AttributeType name="ShipperID"&gt;
  &lt;s:datatype dt:type="int" dt:maxLength="4"/&gt;
&lt;/s:AttributeType&gt;
&lt;s:AttributeType name="CompanyName"&gt;
  &lt;s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/&gt;
&lt;/s:AttributeType&gt;</code>
      <para>The definition allows<codeInline> CompanyName </codeInline>to be null, but<codeInline> ShipperID </codeInline>cannot contain a null value. If the data section contained the following row, the Persistence Provider would set the status of the data for the<codeInline> CompanyName </codeInline>column to the OLE DB status constant DBSTATUS_S_ISNULL:</para>
      <code>&lt;z:row ShipperID="1"/&gt;</code>
      <para>If the row was entirely empty, as follows, the Persistence Provider would return an OLE DB status of DBSTATUS_E_UNAVAILABLE for<codeInline> ShipperID </codeInline>and DBSTATUS_S_ISNULL for CompanyName.</para>
      <code>&lt;z:row/&gt; </code>
      <para>Note that a zero-length string is not the same as null.</para>
      <code>&lt;z:row ShipperID="1" CompanyName=""/&gt;</code>
      <para>For the preceding row, the Persistence Provider will return an OLE DB status of DBSTATUS_S_OK for both columns. The<codeInline> CompanyName </codeInline>in this case is simply "" (a zero-length string).</para>
      <para>For further information about the OLE DB constructs available for use within the schema of an XML document for OLE DB, see the definition of "urn:schemas-microsoft-com:rowset" and the OLE DB Programmer's Guide.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</link>
</relatedTopics>
</developerConceptualDocument>