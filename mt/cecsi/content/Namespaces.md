---
title: "Namespaces"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: efff5569-db52-451d-a039-2e74870534da
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
# Namespaces
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The XML persistence format in ADO uses the following four namespaces.</para>
  </introduction>
  <section>
    <title>Remarks</title>
    <content>
      <para>The XML persistence format in ADO uses the following four namespaces.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Prefix</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>s</para>
            </TD>
            <TD>
              <para>Refers to the "XML-Data" namespace containing the elements and attributes that define the schema of the current Recordset.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>dt</para>
            </TD>
            <TD>
              <para>Refers to the data type definitions specification.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>rs</para>
            </TD>
            <TD>
              <para>Refers to the namespace containing elements and attributes specific to ADO Recordset properties and attributes.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>z</para>
            </TD>
            <TD>
              <para>Refers to the schema of the current rowset.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>A client should not add its own tags to these namespaces, as defined by the specification. For example, a client should not define a namespace as "urn:schemas-microsoft-com:rowset" and then write out something such as "rs:MyOwnTag." To learn more about namespaces, see the <externalLink><linkText>W3C Namespaces in XML Recommendation</linkText><linkUri>http://www.w3.org/TR/REC-xml-names/</linkUri></externalLink>.</para>
      <alert class="important">
        <para>The ID for the schema tag must be "RowsetSchema," and the namespace used to refer to the schema of the current rowset must point to "#RowsetSchema."</para>
      </alert>
      <para>Note that the prefix of the namespace — the part between the colon and the equal sign — is arbitrary.</para>
      <code>xmlns:rs="urn:schemas-microsoft-com:rowset"</code>
      <para>The user can define this to be any name as long as this name is consistently used throughout the XML document. ADO always writes out "s," "rs," "dt," and "z," but these prefix names are not hard-coded into the loading component.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</link>
</relatedTopics>
</developerConceptualDocument>