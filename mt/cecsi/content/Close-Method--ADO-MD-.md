---
title: "Close Method (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
caps.latest.revision: 12
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
# Close Method (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Closes an open cellset.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Cellset</parameterReference><legacyBold>.Close</legacyBold></legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>Using the <unmanagedCodeEntityReference>Close</unmanagedCodeEntityReference> method to close a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object will release the associated data, including data in any related <legacyLink xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell</legacyLink>, <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink>, <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink>, or <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> objects. Closing a <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference> does not remove it from memory; you can change its property settings and open it again later. To completely eliminate an object from memory, set the object variable to <legacyBold>Nothing</legacyBold>.</para>
      <para>You can later call the <legacyLink xlink:href="a87d8080-a238-45e5-bc80-9a8625b3810f">Open</legacyLink> method to reopen the <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference> using the same or another source string. While the <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference> object is closed, retrieving any properties or calling any methods that reference the underlying data or metadata generates an error.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object (ADO MD)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis Object</link>
<link xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell Object</link>
<link xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member Object</link>
<link xlink:href="a87d8080-a238-45e5-bc80-9a8625b3810f">Open Method</link>
<link xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position Object</link>
<link xlink:href="06d480ca-9eb6-4570-a45d-a73539bddd32">State Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>