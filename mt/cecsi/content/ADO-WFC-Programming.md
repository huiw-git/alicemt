---
title: "ADO/WFC Programming"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fdfa42e-897e-4770-b320-ab3720adabcc
caps.latest.revision: 8
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
# ADO/WFC Programming
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>For Microsoft Visual J++ 6.0, ADO has been extended to work with Windows Foundation Classes (WFC) in the following ways. First, a set of Java classes has been implemented that extends the ADO interfaces and creates notifications interesting to the Java programmer; the Java classes also expose functions that return Java types to the user. To improve performance, the Java class directly accesses the native data types in the OLE DB rowset object, and returns them to the Java programmer as Java types without first converting them to and from a variant. ADO has also been extended to work with event notifications in the WFC framework.</para>
    <para>ADO for Windows Foundation Classes (ADO/WFC) supports all the standard ADO methods, properties, objects, and events. However, operations that require a variant as a parameter and show excellent performance in a language such as Microsoft Visual Basic, display lesser performance in a language such as Visual J++. For that reason, ADO/WFC also provides accessor functions on the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object that take native Java data types instead of the variant data type.</para>
    <para>For more detailed information within the ADO documentation about ADO/WFC packages, see <legacyLink xlink:href="a14bbc36-87ec-409d-97b3-393b66b1b8e3">the ADO/WFC Syntax Index</legacyLink>.</para>
    <para>For related information within the Visual J++ documentation, see <externalLink><linkText>Converting Visual Basic ADO Examples to Visual J++</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=5684</linkUri></externalLink>.</para>
  </introduction>
  <section>
    <title>Referencing the Library</title>
    <content>
      <para>To import the ADO/WFC data classes into your project, include the following line in your code:</para>
      <code>import com.ms.wfc.data.*;</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</link>
<link xlink:href="a14bbc36-87ec-409d-97b3-393b66b1b8e3">ADO/WFC Syntax Index</link>
<link xlink:href="f9737a65-4b2f-47fa-b026-1494dca158eb">Using ADO with the Java Type Library Wizard</link>
<link xlink:href="2d7cb5b5-8307-49dd-b07e-c07069bb1626">Using ADO with the Microsoft SDK for Java</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>