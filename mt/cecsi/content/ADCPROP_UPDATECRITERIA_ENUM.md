---
title: "ADCPROP_UPDATECRITERIA_ENUM"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
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
# ADCPROP_UPDATECRITERIA_ENUM
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies which fields can be used to detect conflicts during an optimistic update of a row of the data source with a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
    <para>Use these constants with the <legacyBold>Recordset</legacyBold> "<legacyBold>Update Criteria</legacyBold>" dynamic property, which is referenced in the <legacyLink xlink:href="80d389dd-46ef-459f-b0d4-6f712fc4f32d">ADO Dynamic Property Index</legacyLink> and documented in the <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Microsoft Cursor Service for OLE DB</legacyLink> documentation.</para>
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
              <legacyBold>adCriteriaAllCols</legacyBold>           </para>
          </TD>
          <TD>
            <para>1 </para>
          </TD>
          <TD>
            <para>Detects conflicts if any column of the data source row has been changed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCriteriaKey</legacyBold>           </para>
          </TD>
          <TD>
            <para>0 </para>
          </TD>
          <TD>
            <para>Detects conflicts if the key column of the data source row has been changed, which means that the row has been deleted.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCriteriaTimeStamp</legacyBold>           </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Detects conflicts if the timestamp of the data source row has been changed, which means the row has been accessed after the <legacyBold>Recordset</legacyBold> was obtained.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCriteriaUpdCols</legacyBold>           </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Detects conflicts if any of the columns of the data source row that correspond to updated fields of the <legacyBold>Recordset</legacyBold> have been changed.</para>
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
              <para>AdoEnums.AdcPropUpdateCriteria.ALLCOLS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.AdcPropUpdateCriteria.KEY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.AdcPropUpdateCriteria.TIMESTAMP</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.AdcPropUpdateCriteria.UPDCOLS</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>