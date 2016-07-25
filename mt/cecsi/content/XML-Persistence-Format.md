---
title: "XML Persistence Format"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
caps.latest.revision: 5
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
# XML Persistence Format
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO uses UTF-8 encoding for the XML stream it persists.</para>
    <para>The ADO XML format is broken into two sections, a schema section followed by the data section. The following is an example XML file for the Shippers table from the Northwind database. Various parts of the XML are discussed following the example.</para>
  </introduction>
  <section>
    <title>Remarks</title>
    <content>
      <code>&lt;xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882" 
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882" 
xmlns:rs="urn:schemas-microsoft-com:rowset" 
xmlns:z="#RowsetSchema"&gt; 
  &lt;s:Schema id="RowsetSchema"&gt; 
    &lt;s:ElementType name="row" content="eltOnly" rs:updatable="true"&gt; 
      &lt;s:AttributeType name="ShipperID" rs:number="1" 
        rs:basetable="shippers" rs:basecolumn="ShipperID"
        rs:keycolumn="true"&gt; 
        &lt;s:datatype dt:type="int" dt:maxLength="4" rs:precision="10" 
          rs:fixedlength="true" rs:maybenull="false"/&gt; 
      &lt;/s:AttributeType&gt; 
      &lt;s:AttributeType name="CompanyName" rs:number="2" 
        rs:nullable="true" rs:write="true" rs:basetable="shippers" 
        rs:basecolumn="CompanyName"&gt; 
        &lt;s:datatype dt:type="string" dt:maxLength="40" /&gt; 
      &lt;/s:AttributeType&gt; 
      &lt;s:AttributeType name="Phone" rs:number="3" rs:nullable="true" 
        rs:write="true" rs:basetable="shippers" 
        rs:basecolumn="Phone"&gt; 
        &lt;s:datatype dt:type="string" dt:maxLength="24"/&gt; 
      &lt;/s:AttributeType&gt; 
      &lt;s:extends type="rs:rowbase"/&gt; 
    &lt;/s:ElementType&gt; 
  &lt;/s:Schema&gt; 

  &lt;rs:data&gt; 
    &lt;z:row ShipperID="1" CompanyName="Speedy Express" 
      Phone="(503) 555-9831"/&gt; 
    &lt;z:row ShipperID="2" CompanyName="United Package" 
      Phone="(503) 555-3199"/&gt; 
    &lt;z:row ShipperID="3" CompanyName="Federal Shipping" 
      Phone="(503) 555-9931"/&gt; 
  &lt;/rs:data&gt; 
&lt;/xml&gt;</code>
      <para>The schema shows the declarations of namespaces, the schema section, and the data section. The schema section contains definitions for row, ShipperID, CompanyName, and Phone.</para>
      <para>Schema definitions conform to the <externalLink><linkText>W3C XML-Data specification</linkText><linkUri>http://www.w3.org/TR/1998/NOTE-XML-data/</linkUri></externalLink> and can be fully validated (though validation will not occur in Internet Explorer 5). XML-Data is currently the only supported schema format for Recordset persistence.</para>
      <para>The data section has three rows containing information about shippers. For an empty rowset, the data section may be empty, but the &lt;rs:data&gt; tags must be present. With no data, you could write the tag shorthand as simply &lt;rs:data/&gt;. Any tag prefixed with "rs" indicates that it is in the namespace defined by urn:schemas-microsoft-com:rowset.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</link>
</relatedTopics>
</developerConceptualDocument>