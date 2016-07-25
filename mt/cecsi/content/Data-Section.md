---
title: "Data Section"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43dc42a8-7057-48e6-93d6-880d5c5c51a4
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
# Data Section
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The data section defines the data of the rowset along with any pending updates, insertions, or deletions. The data section can contain zero or more rows. It can only contain data from one rowset where the row is defined by the schema. Also, as noted before, columns without any data can be omitted. If an attribute or subelement is used in the data section and that construct has not been defined in the schema section, it is silently ignored.</para>
  </introduction>
  <section>
    <title>String</title>
    <content>
      <para>Reserved XML characters in text data must be replaced with appropriate character entities. For example, in the company name "Joe's Garage," the single quotation mark must be replaced by an entity. The actual row would resemble the following:</para>
      <code>&lt;z:row CompanyName="Joe&amp;apos;s Garage"/&gt;</code>
      <para>The following characters are reserved in XML and must be replaced by character entities: {',",&amp;,&lt;,&gt;}.</para>
    </content>
  </section>
  <section>
    <title>Binary</title>
    <content>
      <para>Binary data is bin.hex encoded (that is, one byte maps to two characters, one character per nibble).</para>
    </content>
  </section>
  <section>
    <title>DateTime</title>
    <content>
      <para>The variant VT_DATE format is not directly supported by XML-Data data types. The correct format for dates with both a data and time component is yyyy-mm-ddThh:mm:ss.</para>
      <para>For more information about date formats specified by XML, see the <externalLink><linkText>W3C XML-Data specification</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=5692</linkUri></externalLink>.</para>
      <para>When the XML-Data specification defines two equivalent data types (for example, i4 == int), ADO will write out the friendly name but read in both.</para>
    </content>
  </section>
  <section>
    <title>Managing Pending Changes</title>
    <content>
      <para>A Recordset can be opened in immediate or batch update mode. When they are opened in batch update mode with client-side cursors, all changes made to the Recordset are in a pending state until the UpdateBatch method is called. Pending changes are also persisted when the Recordset is saved. In XML, they are represented by the use of the "update" elements defined in urn:schemas-microsoft-com:rowset. In addition, if a rowset can be updated, the updatable property must be set to true in the definition of the row. For example, to define that the Shippers table contains pending changes, the row definition would look resemble following.</para>
      <code>&lt;s:ElementType name="row" content="eltOnly" updatable="true"&gt;
  &lt;s:attribute type="ShipperID"/&gt;
  &lt;s:attribute type="CompanyName"/&gt;
  &lt;s:attribute type="Phone"/&gt;
  &lt;s:extends type="rs:rowbase"/&gt;
&lt;/s:ElementType&gt;</code>
      <para>This tells the Persistence Provider to surface data so that ADO can construct an updatable Recordset object.</para>
      <para>The following sample data shows how insertions, changes, and deletions look in the persisted file.</para>
      <code>&lt;rs:data&gt;
  &lt;z:row ShipperID="2" CompanyName="United Package" 
    Phone="(503) 555-3199"/&gt;
&lt;rs:update&gt;
  &lt;rs:original&gt;
    &lt;z:row ShipperID="3" CompanyName="Federal Shipping" 
      Phone="(503) 555-9931"/&gt;
  &lt;/rs:original&gt;
  &lt;z:row Phone="(503) 552-7134"/&gt;
&lt;/rs:update&gt;
&lt;rs:insert&gt;
  &lt;z:row ShipperID="12" CompanyName="Lightning Shipping" 
    Phone="(505) 111-2222"/&gt;
  &lt;z:row ShipperID="13" CompanyName="Thunder Overnight" 
    Phone="(505) 111-2222"/&gt;
  &lt;z:row ShipperID="14" CompanyName="Blue Angel Air Delivery" 
    Phone="(505) 111-2222"/&gt;
&lt;/rs:insert&gt;
&lt;rs:delete&gt;
  &lt;z:row ShipperID="1" CompanyName="Speedy Express" Phone="(503) 555-9831"/&gt;
&lt;/rs:delete&gt;
&lt;/rs:data&gt;</code>
      <para>An update always contains the entire original row data followed by the changed row data. The changed row may contain all the columns or only those columns that have actually changed. In the previous example, the row for Shipper 2 is not changed, and only the Phone column has changed values for Shipper 3 and is therefore the only column included in the changed row. The inserted rows for Shippers 12, 13, and 14 are batched together under one rs:insert tag. Note that deleted rows can also be batched together, although this is not shown in the previous example.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</link>
</relatedTopics>
</developerConceptualDocument>