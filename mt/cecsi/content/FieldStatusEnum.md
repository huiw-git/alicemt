---
title: "FieldStatusEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e06da1e2-303f-41b2-a3b0-61e233da152c
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
# FieldStatusEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the <legacyLink xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">status</legacyLink> of a <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>. </para>
    <para>The <legacyBold>adFieldPending*</legacyBold> values indicate the operation that caused the status to be set, and may be combined with other status values.</para>
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
              <legacyBold>adFieldAlreadyExists</legacyBold>
            </para>
          </TD>
          <TD>
            <para>26</para>
          </TD>
          <TD>
            <para>Indicates that the specified field already exists.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldBadStatus</legacyBold>
            </para>
          </TD>
          <TD>
            <para>12</para>
          </TD>
          <TD>
            <para>Indicates that an invalid status value was sent from ADO to the OLE DB provider. Possible causes include an OLE DB 1.0 or 1.1 provider, or an improper combination of <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> and <legacyLink xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">Status</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldCannotComplete</legacyBold>
            </para>
          </TD>
          <TD>
            <para>20</para>
          </TD>
          <TD>
            <para>Indicates that the server of the URL specified by <legacyLink xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source</legacyLink> could not complete the operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldCannotDeleteSource</legacyBold>
            </para>
          </TD>
          <TD>
            <para>23</para>
          </TD>
          <TD>
            <para>Indicates that during a move operation, a tree or subtree was moved to a new location, but the source could not be deleted.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldCantConvertValue</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates that the field cannot be retrieved or stored without loss of data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldCantCreate</legacyBold>
            </para>
          </TD>
          <TD>
            <para>7</para>
          </TD>
          <TD>
            <para>Indicates that the field could not be added because the provider exceeded a limitation (such as the number of fields allowed).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldDataOverflow</legacyBold>
            </para>
          </TD>
          <TD>
            <para>6</para>
          </TD>
          <TD>
            <para>Indicates that the data returned from the provider overflowed the data type of the field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldDefault</legacyBold>
            </para>
          </TD>
          <TD>
            <para>13</para>
          </TD>
          <TD>
            <para>Indicates that the default value for the field was used when setting data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldDoesNotExist</legacyBold>
            </para>
          </TD>
          <TD>
            <para>16</para>
          </TD>
          <TD>
            <para>Indicates that the field specified does not exist.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldIgnore</legacyBold>
            </para>
          </TD>
          <TD>
            <para>15</para>
          </TD>
          <TD>
            <para>Indicates that this field was skipped when setting data values in the source. The provider set no value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldIntegrityViolation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>10</para>
          </TD>
          <TD>
            <para>Indicates that the field cannot be modified because it is a calculated or derived entity.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldInvalidURL</legacyBold>
            </para>
          </TD>
          <TD>
            <para>17</para>
          </TD>
          <TD>
            <para>Indicates that the data source URL contains invalid characters.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldIsNull</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Indicates that the provider returned a VARIANT value of type VT_NULL and that the field is not empty.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldOK</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Default. Indicates that the field was successfully added or deleted.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldOutOfSpace</legacyBold>
            </para>
          </TD>
          <TD>
            <para>22</para>
          </TD>
          <TD>
            <para>Indicates that the provider is unable to obtain enough storage space to complete a move or copy operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldPendingChange</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x40000</para>
          </TD>
          <TD>
            <para>Indicates either that the field has been deleted and then re-added, perhaps with a different data type, or that the value of the field which previously had a status of <legacyBold>adFieldOK</legacyBold> has changed. The final form of the field will modify the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection after the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method is called.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldPendingDelete</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x20000</para>
          </TD>
          <TD>
            <para>Indicates that the <legacyBold>Delete</legacyBold> operation caused the status to be set. The field has been marked for deletion from the <legacyBold>Fields</legacyBold> collection after the <legacyBold>Update</legacyBold> method is called. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldPendingInsert</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10000</para>
          </TD>
          <TD>
            <para>Indicates that the <legacyBold>Append </legacyBold>operation caused the status to be set. The <legacyBold>Field</legacyBold> has been marked to be added to the <legacyBold>Fields</legacyBold> collection after the <legacyBold>Update</legacyBold> method is called.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldPendingUnknown</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x80000</para>
          </TD>
          <TD>
            <para>Indicates that the provider cannot determine what operation caused field status to be set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldPendingUnknownDelete</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x100000</para>
          </TD>
          <TD>
            <para>Indicates that the provider cannot determine what operation caused field status to be set, and that the field will be deleted from the <legacyBold>Fields</legacyBold> collection after the <legacyBold>Update</legacyBold> method is called.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldPermissionDenied</legacyBold>
            </para>
          </TD>
          <TD>
            <para>9</para>
          </TD>
          <TD>
            <para>Indicates that the field cannot be modified because it is defined as read-only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldReadOnly</legacyBold>
            </para>
          </TD>
          <TD>
            <para>24</para>
          </TD>
          <TD>
            <para>Indicates that the field in the data source is defined as read-only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldResourceExists</legacyBold>
            </para>
          </TD>
          <TD>
            <para>19</para>
          </TD>
          <TD>
            <para>Indicates that the provider was unable to perform the operation because an object already exists at the destination URL and it is not able to overwrite the object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldResourceLocked</legacyBold>
            </para>
          </TD>
          <TD>
            <para>18</para>
          </TD>
          <TD>
            <para>Indicates that the provider was unable to perform the operation because the data source is locked by one or more other application or process.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldResourceOutOfScope</legacyBold>
            </para>
          </TD>
          <TD>
            <para>25</para>
          </TD>
          <TD>
            <para>Indicates that a source or destination URL is outside the scope of the current record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldSchemaViolation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>11</para>
          </TD>
          <TD>
            <para>Indicates that the value violated the data source schema constraint for the field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldSignMismatch</legacyBold>
            </para>
          </TD>
          <TD>
            <para>5</para>
          </TD>
          <TD>
            <para>Indicates that data value returned by the provider was signed but the data type of the ADO field value was unsigned.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldTruncated</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Indicates that variable-length data was truncated when reading from the data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldUnavailable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>8</para>
          </TD>
          <TD>
            <para>Indicates that the provider could not determine the value when reading from the data source. For example, the row was just created, the default value for the column was not available, and a new value had not yet been specified.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFieldVolumeNotFound</legacyBold>
            </para>
          </TD>
          <TD>
            <para>21</para>
          </TD>
          <TD>
            <para>Indicates that the provider is unable to locate the storage volume indicated by the URL.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>These constants do not have ADO/WFC equivalents.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">Status Property (ADO Field)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>