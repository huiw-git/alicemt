---
title: "Charset Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
caps.latest.revision: 15
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
# Charset Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the character set into which the contents of a text <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> should be translated for storage in the internal buffer of the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value that specifies the character set into which the contents of the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> will be translated. The default value is <legacyBold>Unicode</legacyBold>. Allowed values are typical strings passed over the interface as Internet character set names (for example, "iso-8859-1", "Windows-1252", and so on). For a list of the character set names that are known by a system, see the subkeys of HKEY_CLASSES_ROOT\MIME\Database\Charset in the Windows Registry.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>In a text <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> object, text data is stored in the character set specified by the <unmanagedCodeEntityReference>Charset</unmanagedCodeEntityReference> property. The default is Unicode. The <unmanagedCodeEntityReference>Charset</unmanagedCodeEntityReference> property is used for converting data going into the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> or coming out of the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference>. For example, if the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> contains ISO-8859-1 data and that data is copied to a BSTR, the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> object will convert the data to Unicode. The reverse is also true.</para>
      <para>For an open <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference>, the current <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> must be at the beginning of the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> (0) to be able to set <unmanagedCodeEntityReference>Charset</unmanagedCodeEntityReference>.</para>
      <para>
        <unmanagedCodeEntityReference>Charset</unmanagedCodeEntityReference> is used only with text <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> objects (<legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> is <legacyBold>adTypeText</legacyBold>). This property is ignored if <unmanagedCodeEntityReference>Type</unmanagedCodeEntityReference> is <legacyBold>adTypeBinary</legacyBold>.</para>
      <para>For a code sample, see <link xlink:href="cb4273e2-c907-4a86-a621-3bf110088228">Step 4: Populate the Details Text Box</link>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>