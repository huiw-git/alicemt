---
title: "ParentURL Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
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
# ParentURL Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates an absolute URL string that points to the parent <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> of the current <legacyBold>Record</legacyBold> object.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <legacyBold>String</legacyBold> value that indicates the URL of the parent <legacyBold>Record</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>ParentURL</legacyBold> property depends on the source used to open the <legacyBold>Record</legacyBold> object. For example, the <legacyBold>Record</legacyBold> can be opened with a source that contains a relative path name of a directory referenced by the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property.</para>
      <para>Suppose "second" is a folder contained under "first". Open the <legacyBold>Record</legacyBold> object by using the following syntax:</para>
      <code>record.ActiveConnection = "http://first"
record.Open "second"</code>
      <para>Now, the value of <codeInline>the </codeInline><legacyBold>ParentURL</legacyBold> property is <codeInline>"http://first"</codeInline>, the same as <legacyBold>ActiveConnection</legacyBold>.</para>
      <para>The source can also be an absolute URL such as, <codeInline>"http://first/second"</codeInline>. The <legacyBold>ParentURL</legacyBold> property is then <codeInline>"http://first"</codeInline>, the level above <codeInline>"second"</codeInline>.</para>
      <para>This property may be a null value if:  </para>
      <list class="bullet">
        <listItem>
          <para>There is no parent for the current object; for example, if the <legacyBold>Record</legacyBold> object represents the root of a directory.</para>
        </listItem>
        <listItem>
          <para>The <legacyBold>Record</legacyBold> object represents an entity that cannot be specified with a URL.</para>
        </listItem>
      </list>
      <para>This property is read-only.</para>
      <alert class="note">
        <para>This property is only supported by document source providers, such as the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="77f95e0a-0cf2-411a-a792-593f77330fbd">Records and Provider-Supplied Fields</legacyLink>.</para>
      </alert>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
      <alert class="note">
        <para>If the current record contains a data record from an ADO <legacyBold>Recordset</legacyBold>, accessing the <legacyBold>ParentURL</legacyBold> property causes a run-time error, indicating that no URL is possible.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>