---
title: "InvokeService (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
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
# InvokeService (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns a pointer to the requested interface on a more capable version of the object.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to  <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
object.<legacyBold>InvokeService</legacyBold>(REFID <parameterReference>riid</parameterReference>, IUknown* <parameterReference>punkNotSoFunctionalInterface</parameterReference>, IUknown** <parameterReference>ppunkMoreFunctionalInterface</parameterReference>) As HRESULT</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <para>
        <parameterReference>riid</parameterReference>
      </para>
      <para>[in] The identifier of the interface being requested.</para>
      <para>
        <parameterReference>punkNotSoFunctionalInterface</parameterReference>
      </para>
      <para>[in] The less capable source object.</para>
      <para>
        <parameterReference>ppunkMoreFunctionalInterface</parameterReference>
      </para>
      <para>[out] The address of the pointer variable that receives the interface pointer requested in <parameterReference>riid</parameterReference>. Upon successful return, the <parameterReference>ppunkMoreFunctionalInterface</parameterReference> parameter contains the requested interface pointer to the object. If the object does not support the interface specified in <parameterReference>riid</parameterReference>, <parameterReference>ppunkMoreFunctionalInterface</parameterReference> is set to NULL.</para>
    </content>
  </parameters>
  <returnValue>
    <content>
      <para>An HRESULT value that indicates if the call to the <legacyBold>InvokeService</legacyBold> method was successful. </para>
    </content>
  </returnValue>
  <languageReferenceRemarks>
    <content>
      <para>The RDS cursor engine implementation of <legacyBold>InvokeService</legacyBold> takes the input rowset (or multiple results object), populates the cursor engine from the input rowset, and then returns a pointer on itself.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="01044c3a-ed38-4144-bc43-fe38a6d22d04">IRDSService Interface (RDS)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="c2c6af1a-3c44-4c9d-ad33-b381552c71af">RDS Methods</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>