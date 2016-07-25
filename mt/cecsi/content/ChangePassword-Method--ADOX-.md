---
title: "ChangePassword Method (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
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
# ChangePassword Method (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Changes the password for a <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">user</legacyLink> account.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>User</parameterReference><legacyBold>.ChangePassword </legacyBold><parameterReference>OldPassword</parameterReference><legacyBold>,</legacyBold> <parameterReference>NewPassword</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>OldPassword </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that specifies the user's existing password. If the user doesn't currently have a password, use an empty string ("") for <parameterReference>OldPassword</parameterReference>.</para>
        </definition>
        <definedTerm> <parameterReference>NewPassword </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that specifies the new password.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>For security reasons, the old password must be specified in addition to the new password.</para>
      <para>An error will occur if the provider does not support the administration of trustee properties.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User Object (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="c9426757-9cdd-4a95-b506-d3d011569109">Groups and Users Append, ChangePassword Methods Example (VB)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>