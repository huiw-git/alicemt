---
title: "FieldAttributeEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
caps.latest.revision: 11
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
# FieldAttributeEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies one or more attributes of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object.</para>
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
              <legacyBold>adFldCacheDeferred</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x1000</para>
          </TD>
          <TD>
            <para>Indicates that the provider caches field values and that subsequent reads are done from the cache.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldFixed</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10</para>
          </TD>
          <TD>
            <para>Indicates that the field contains fixed-length data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldIsChapter</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2000</para>
          </TD>
          <TD>
            <para>Indicates that the field contains a chapter value, which specifies a specific child recordset related to this parent field. Typically chapter fields are used with data shaping or filters.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldIsCollection</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x40000</para>
          </TD>
          <TD>
            <para>Indicates that the field specifies that the resource represented by the record is a collection of other resources, such as a folder, rather than a simple resource, such as a text file.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldKeyColumn</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x8000</para>
          </TD>
          <TD>
            <para>Indicates that the field specifies all or part of the column's primary key.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldIsDefaultStream</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x20000</para>
          </TD>
          <TD>
            <para>Indicates that the field contains the default stream for the resource represented by the record. For example, the default stream can be the HTML content of a root folder on a Web site, which is automatically served when the root URL is specified.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldIsNullable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x20</para>
          </TD>
          <TD>
            <para>Indicates that the field accepts null values.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldIsRowURL</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10000</para>
          </TD>
          <TD>
            <para>Indicates that the field contains the URL that names the resource from the data store represented by the record. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldLong</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x80</para>
          </TD>
          <TD>
            <para>Indicates that the field is a long binary field. Also indicates that you can use the <legacyLink xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk</legacyLink> and <legacyLink xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk</legacyLink> methods.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldMayBeNull</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x40</para>
          </TD>
          <TD>
            <para>Indicates that you can read null values from the field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldMayDefer</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2</para>
          </TD>
          <TD>
            <para>Indicates that the field is deferred—that is, the field values are not retrieved from the data source with the whole record, but only when you explicitly access them.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldNegativeScale</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>Indicates that the field represents a numeric value from a column that supports negative scale values. The scale is specified by the <legacyLink xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale</legacyLink> property.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldRowID</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x100</para>
          </TD>
          <TD>
            <para>Indicates that the field contains a persistent row identifier that cannot be written to and has no meaningful value except to identify the row (such as a record number, unique identifier, and so forth).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldRowVersion</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x200</para>
          </TD>
          <TD>
            <para>Indicates that the field contains some kind of time or date stamp used to track updates.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldUnknownUpdatable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x8</para>
          </TD>
          <TD>
            <para>Indicates that the provider cannot determine if you can write to the field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1 0xFFFFFFFF</para>
          </TD>
          <TD>
            <para>Indicates that the provider does not specify the field attributes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFldUpdatable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x4</para>
          </TD>
          <TD>
            <para>Indicates that you can write to the field.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.CACHEDEFERRED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.FIXED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.ISNULLABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.LONG</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.MAYBENULL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.MAYDEFER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.NEGATIVESCALE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.ROWID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.ROWVERSION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.UNKNOWNUPDATABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.UNSPECIFIED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FieldAttribute.UPDATABLE</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>