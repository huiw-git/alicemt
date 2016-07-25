---
title: "RecordOpenOptionsEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
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
# RecordOpenOptionsEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies options for opening a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>. These values may be combined by using OR.</para>
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
              <legacyBold>adDelayFetchFields</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x8000</para>
          </TD>
          <TD>
            <para>Indicates to the provider that the fields associated with the <legacyBold>Record</legacyBold> need not be retrieved initially, but can be retrieved at the first attempt to access the field. The default behavior, indicated by the absence of this flag, is to retrieve all the <legacyBold>Record</legacyBold> object fields.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDelayFetchStream</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>Indicates to the provider that the default stream associated with the <legacyBold>Record</legacyBold> need not be retrieved initially. The default behavior, indicated by the absence of this flag, is to retrieve the default stream associated with the <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adOpenAsync</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x1000</para>
          </TD>
          <TD>
            <para>Indicates that the <legacyBold>Record</legacyBold> object is opened in asynchronous mode.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adOpenExecuteCommand</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10000</para>
          </TD>
          <TD>
            <para>Indicates that the Source string contains command text that should be executed. This value is equivalent to the <legacyBold>adCmdText</legacyBold> option on <legacyBold>Recordset.Open</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adOpenRecordUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Default. Indicates no options are specified.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adOpenOutput</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x800000</para>
          </TD>
          <TD>
            <para>Indicates that if the source points to a node that contains an executable script (such as an .ASP page), then the opened <legacyBold>Record</legacyBold> will contain the results of the executed script. This value is only valid with non-collection records.</para>
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
        <link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>