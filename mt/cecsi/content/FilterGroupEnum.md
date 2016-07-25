---
title: "FilterGroupEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
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
# FilterGroupEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the group of records to be filtered from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
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
              <legacyBold>adFilterAffectedRecords</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Filters for viewing only records affected by the last <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink>, <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>, <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>, or <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> call.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFilterConflictingRecords</legacyBold>
            </para>
          </TD>
          <TD>
            <para>5</para>
          </TD>
          <TD>
            <para>Filters for viewing the records that failed the last batch update.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFilterFetchedRecords</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Filters for viewing the records in the current cache—that is, the results of the last call to retrieve records from the database.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFilterNone</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Removes the current filter and restores all records for viewing.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFilterPendingRecords</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Filters for viewing only records that have changed but have not yet been sent to the server. Applicable only for batch update mode.</para>
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
              <para>AdoEnums.FilterGroup.AFFECTEDRECORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FilterGroup.CONFLICTINGRECORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FilterGroup.FETCHEDRECORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FilterGroup.NONE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.FilterGroup.PENDINGRECORDS</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter Property</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>