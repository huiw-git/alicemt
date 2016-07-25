---
title: "Property Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: 5
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
# Property Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a characteristic of an ADOX object.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>ADOX objects have two types of properties: built-in and dynamic.</para>
      <para>Built-in properties are those properties immediately available to any new object, using the MyObject.Property syntax. They do not appear as Property objects in an object's <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties collection</legacyLink>, so although you can change their values, you cannot modify their characteristics.</para>
      <para>Dynamic properties are defined by the underlying data provider, and appear in the Properties collection for the appropriate ADOX object.  Dynamic properties can be referenced only through the collection, using the MyObject.Properties(0) or MyObject.Properties("Name") syntax.</para>
      <para>You cannot delete either kind of property.</para>
      <para>A dynamic Property object has four built-in properties of its own: </para>
      <para>The <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property is a string that identifies the property.</para>
      <para>The <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property is an integer that specifies the property data type.</para>
      <para>The <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property is a variant that contains the property setting. Value is the default property for a Property object.</para>
      <para>The <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property is a long value that indicates characteristics of the property specific to the provider.</para>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="640780dc-5733-4f0c-9c11-6f43c1db5901">ADOX Property Object Properties, Methods, and Events</link>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>