---
title: "DateModified Property (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
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
# DateModified Property (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the date the object was last modified.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <languageKeyword>Variant</languageKeyword> value specifying the date modified. The value is null if <legacyBold>DateModified</legacyBold> is not supported by the provider.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>DateModified</legacyBold> property is null for newly appended objects. After appending a new <legacyLink xlink:href="653421ce-7b94-43d0-9bc6-4900f8f2af45">View</legacyLink> or <legacyLink xlink:href="927bcf3e-32f5-4a80-98d3-600779f0732e">Procedure</legacyLink>, you must call the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method of the <legacyLink xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views</legacyLink> or <legacyLink xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures</legacyLink> collection to obtain values for the <legacyBold>DateModified</legacyBold> property.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="927bcf3e-32f5-4a80-98d3-600779f0732e">Procedure Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="653421ce-7b94-43d0-9bc6-4900f8f2af45">View Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d608ea35-6e68-402f-8184-a5041e408678">DateCreated and DateModified Properties Example (VB)</link>
<link xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>