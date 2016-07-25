---
title: "Records and Provider-Supplied Fields"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77f95e0a-0cf2-411a-a792-593f77330fbd
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
# Records and Provider-Supplied Fields
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object is opened, its source can be the current row of an open <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, an absolute URL, or a relative URL in conjunction with an open <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
    <para>If the <legacyBold>Record</legacyBold> is opened from a <legacyBold>Recordset</legacyBold>, the <legacyBold>Record</legacyBold> object <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection will contain all the fields from the <legacyBold>Recordset</legacyBold>, plus any fields added by the underlying provider.</para>
    <para>The provider may insert additional fields that serve as supplementary characteristics of the <legacyBold>Record</legacyBold>. As a result, a <legacyBold>Record</legacyBold> may have unique fields not in the <legacyBold>Recordset</legacyBold> as a whole or any <legacyBold>Record</legacyBold> derived from another row of the <legacyBold>Recordset</legacyBold>.</para>
    <para>For example, all rows of a <legacyBold>Recordset</legacyBold> derived from an e-mail data source might have columns such as From, To, and Subject. A <legacyBold>Record</legacyBold> derived from that <legacyBold>Recordset</legacyBold> will have the same fields. However, the <legacyBold>Record</legacyBold> may also have other fields unique to the particular message represented by that <legacyBold>Record</legacyBold>, such as Attachment and Cc (carbon copy).</para>
    <para>Although the <legacyBold>Record</legacyBold> object and current row of the <legacyBold>Recordset</legacyBold> have the same fields, they are different because <legacyBold>Record</legacyBold> and <legacyBold>Recordset</legacyBold> objects have different methods and properties.</para>
    <para>A field held in common by the <legacyBold>Record</legacyBold> and <legacyBold>Recordset</legacyBold> can be modified on either object. However, the field cannot be deleted on the <legacyBold>Record</legacyBold> object, although the underlying provider may support setting the field to null.</para>
    <para>After the <legacyBold>Record</legacyBold> is opened, you can programmatically add fields. You can also delete fields that you have added, but you cannot delete fields from the original <legacyBold>Recordset</legacyBold>.</para>
    <para>You can also open the <legacyBold>Record</legacyBold> object directly from a URL. In this case, the fields added to the <legacyBold>Record</legacyBold> depend on the underlying provider. Currently, most providers add a set of fields that describe the entity represented by the <legacyBold>Record</legacyBold>. If the entity consists of a stream of bytes, such as a simple file, a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object can usually be opened from the <legacyBold>Record</legacyBold>.</para>
  </introduction>
  <section>
    <title>Special Fields for Document Source Providers</title>
    <content>
      <para>A special class of providers, called <legacyItalic>document source providers</legacyItalic>, manages folders and documents. When a <legacyBold>Record</legacyBold> object represents a document or a <legacyBold>Recordset</legacyBold> object represents a folder of documents, the document source provider populates those objects with a unique set of fields that describe characteristics of the document instead of the actual document itself. Typically, one field contains a reference to the <legacyBold>Stream</legacyBold> that represents the document.</para>
      <para>These fields constitute a resource <legacyBold>record</legacyBold> or <legacyBold>recordset</legacyBold> and are listed for the specific providers that support them in <legacyLink xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</legacyLink>.</para>
      <para>Two constants index the <legacyBold>Fields</legacyBold> collection of a resource <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold> to retrieve a pair of commonly used fields. The <legacyBold>Field</legacyBold> object <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property returns the desired content.  </para>
      <list class="bullet">
        <listItem>
          <para>The field accessed with the <legacyBold>adDefaultStream</legacyBold> constant contains a default stream associated with the <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold> object. The provider assigns a default stream to an object.</para>
        </listItem>
        <listItem>
          <para>The field accessed with the <legacyBold>adRecordURL</legacyBold> constant contains the absolute URL that identifies the document.</para>
        </listItem>
      </list>
      <para>A document source provider does not support the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection of <legacyBold>Record</legacyBold> and <legacyBold>Field</legacyBold> objects. The content of the <legacyBold>Properties</legacyBold> collection is null for such objects.</para>
      <para>A document source provider may add a provider-specific property such as <legacyBold>Datasource Type</legacyBold> to identify whether it is a document source provider. For more information about how to determine your type of provider, see your provider documentation.</para>
    </content>
  </section>
  <section>
    <title>Resource Recordset Columns</title>
    <content>
      <para>A <legacyItalic>resource recordset </legacyItalic>consists of the following columns.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Column name</para>
            </TD>
            <TD>
              <para>Type </para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>RESOURCE_PARSENAME</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Read-only. Indicates the URL of the resource.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_PARENTNAME</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Read-only. Indicates the absolute URL of the parent record.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_ABSOLUTEPARSENAME</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Read-only. Indicates the absolute URL of the resource, which is the concatenation of PARENTNAME and PARSENAME.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_ISHIDDEN</para>
            </TD>
            <TD>
              <para>AdBoolean</para>
            </TD>
            <TD>
              <para>True if the resource is hidden. No rows will be returned unless the command that creates the rowset explicitly selects rows where RESOURCE_ISHIDDEN is True.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_ISREADONLY</para>
            </TD>
            <TD>
              <para>AdBoolean</para>
            </TD>
            <TD>
              <para>True if the resource is read-only. Tries to open this resource with DBBINDFLAG_WRITE and will fail with DB_E_READONLY. This property can be edited even when the resource has only been opened for reading.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_CONTENTTYPE</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Indicates the likely use of the document—for example, a lawyer's brief. This may correspond to the Office template that was used to create the document.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_CONTENTCLASS</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Indicates the MIME type of the document, indicating the format such as "<codeInline>text/html</codeInline>".</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_CONTENTLANGUAGE</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Indicates the language in which the content is stored.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_CREATIONTIME</para>
            </TD>
            <TD>
              <para>adFileTime </para>
            </TD>
            <TD>
              <para>Read-only. Indicates a FILETIME structure that contains the time the resource was created. The time is reported in Coordinated Universal Time (UTC) format.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_LASTACCESSTIME</para>
            </TD>
            <TD>
              <para>AdFileTime</para>
            </TD>
            <TD>
              <para>Read-only. Indicates a FILETIME structure that contains the time that the resource was last accessed. The time is in UTC format. The FILETIME members are zero if the provider does not support this time member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_LASTWRITETIME</para>
            </TD>
            <TD>
              <para>AdFileTime</para>
            </TD>
            <TD>
              <para>Read-only. Indicates a FILETIME structure that contains the time that the resource was last written. The time is in UTC format. The FILETIME members are zero if the provider does not support this time member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_STREAMSIZE</para>
            </TD>
            <TD>
              <para>asUnsignedBigInt</para>
            </TD>
            <TD>
              <para>Read-only. Indicates the size of the resource's default stream, in bytes.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_ISCOLLECTION</para>
            </TD>
            <TD>
              <para>AdBoolean</para>
            </TD>
            <TD>
              <para>Read-only. True if the resource is a collection, such as a directory. False if the resource is a simple file. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_ISSTRUCTUREDDOCUMENT</para>
            </TD>
            <TD>
              <para>AdBoolean</para>
            </TD>
            <TD>
              <para>True if the resource is a structured document. False if the resource is not a structured document. It could be a collection or a simple file.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DEFAULT_DOCUMENT</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Read-only. Indicates that this resource contains a URL to the default simple document of a folder or a structured document. Used when the default stream is requested from a resource. This property is blank for a simple file.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CHAPTERED_CHILDREN</para>
            </TD>
            <TD>
              <para>AdChapter</para>
            </TD>
            <TD>
              <para>Read-only. Optional. Indicates the chapter of the rowset that contains the children of the resource. (The <legacyItalic>OLE DB Provider for Internet Publishing</legacyItalic> does not use this column.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_DISPLAYNAME</para>
            </TD>
            <TD>
              <para>AdVarWChar</para>
            </TD>
            <TD>
              <para>Read-only. Indicates the display name of the resource.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESOURCE_ISROOT</para>
            </TD>
            <TD>
              <para>AdBoolean</para>
            </TD>
            <TD>
              <para>Read-only. True if the resource is the root of a collection or structured document.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>