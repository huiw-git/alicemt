---
title: "Field-Related Error Information"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
caps.latest.revision: 3
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
# Field-Related Error Information
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If an error is directly related to a field — for example, if the data is missing or if it is the wrong type for the field — you can retrieve more information about the cause of the problem by examining the <legacyBold>Field</legacyBold> object's <legacyBold>Status</legacyBold> property. This property has been enhanced to provide specific information about the problem. So, for example, when a call to <legacyBold>UpdateBatch</legacyBold> fails, the cause of the problem can be determined by examining the <legacyBold>Status</legacyBold> property of the <legacyBold>Fields</legacyBold> in each of the effected records. The property will contain one of the values in the <legacyBold>FieldStatusEnum</legacyBold> constant. The following table includes those values that are of particular interest when an error occurs.</para>
  </introduction>
  <section>
    <content>
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
              <legacyBold>adFieldIgnore</legacyBold>
            </para>
            </TD>
            <TD>
              <para>15</para>
            </TD>
            <TD>
              <para>Indicates that this field was skipped when setting data values in the source. No value was set by the provider.</para>
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
              <legacyBold>adFieldIsNull</legacyBold>
            </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Indicates that the provider returned a null value.</para>
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
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>