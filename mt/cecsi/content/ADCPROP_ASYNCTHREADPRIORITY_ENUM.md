---
title: "ADCPROP_ASYNCTHREADPRIORITY_ENUM"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
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
# ADCPROP_ASYNCTHREADPRIORITY_ENUM
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>For an RDS <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, specifies the execution priority of the asynchronous thread that retrieves data.</para>
    <para>Use these constants with the <legacyBold>Recordset</legacyBold> "<legacyBold>Background Thread Priority</legacyBold>" dynamic property, which is referenced in the ADO-to-OLE DB Dynamic Property index and documented in the <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Microsoft Cursor Service for OLE DB</legacyLink> documentation.</para>
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
              <legacyBold>adPriorityAboveNormal</legacyBold>           </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Sets priority between normal and highest.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPriorityBelowNormal</legacyBold>           </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Sets priority between lowest and normal.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPriorityHighest</legacyBold>           </para>
          </TD>
          <TD>
            <para>5</para>
          </TD>
          <TD>
            <para>Sets priority to the highest possible.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>AdPriorityLowest</legacyBold>           </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Sets priority to the lowest possible.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPriorityNormal</legacyBold>           </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Sets priority to normal.</para>
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
              <para>AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.AdcPropAsyncThreadPriority.HIGHEST </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.AdcPropAsyncThreadPriority.LOWEST </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.AdcPropAsyncThreadPriority.NORMAL </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>