---
title: "Referencing the ADO Libraries In a Visual Basic 6 Application"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
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
# Referencing the ADO Libraries In a Visual Basic 6 Application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To import the ADO libraries into a Microsoft Visual Basic 6 application, you must set a reference in the Visual Basic project.</para>
    <procedure>
      <title>To set a reference to the ADO libraries in a Visual Basic project</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Create a new or open an existing Visual Basic project.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Click the <legacyBold>Project </legacyBold>menu item and then select <legacyBold>References...</legacyBold> from the drop-down menu panel.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From <legacyBold>Available References</legacyBold>, check the box for <legacyBold>Microsoft ActiveX Data Objects </legacyBold><legacyBold><legacyItalic>n.n</legacyItalic></legacyBold><legacyBold> Library</legacyBold>, where <legacyBold><legacyItalic>n.n</legacyItalic></legacyBold> represents the latest version number. The <legacyBold>Location</legacyBold> field below should identify your choice as <legacyItalic>$installDir\msado15.dll</legacyItalic>, where <legacyItalic>$installDir </legacyItalic>represents the path of the directory in which the ADO library has been installed.</para>
          </content>
        </step>
        <step>
          <content>
            <para>If you intend to use ADO MD, repeat step 3 to select <legacyBold>Microsoft ActiveX Data Objects (Multi-dimensional) </legacyBold><legacyBold><legacyItalic>n.n</legacyItalic></legacyBold><legacyBold> Library</legacyBold>. The <legacyBold>Location</legacyBold> field should identify this choice as <legacyItalic>$installDir\msadomd.dll</legacyItalic>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>If you intend to use ADOX, repeat step 3 to select <legacyBold>Microsoft ADO Ext. </legacyBold><legacyBold><legacyItalic>n.n</legacyItalic></legacyBold><legacyBold> for DDL and Security</legacyBold>. The <legacyBold>Location</legacyBold> field should identify this choice as <legacyItalic>$installDir\msadox.dll</legacyItalic>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Click <legacyBold>OK</legacyBold> to finish setting the references.</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <section>
    <title>Backward Compatibility</title>
    <content>
      <para>Installing ADO also copies the following type libraries of earlier versions:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyItalic>msado27.tlb</legacyItalic>, ADO 2.7 Type Library</para>
        </listItem>
        <listItem>
          <para>
            <legacyItalic>msado26.tlb</legacyItalic>, ADO 2.6 Type Library</para>
        </listItem>
        <listItem>
          <para>
            <legacyItalic>msado25.tlb</legacyItalic>, ADO 2.5 Type Library</para>
        </listItem>
        <listItem>
          <para>
            <legacyItalic>msado21.tlb</legacyItalic>, ADO 2.1 Type Library</para>
        </listItem>
        <listItem>
          <para>
            <legacyItalic>msado20.tlb</legacyItalic>, ADO 2.0 Type Library</para>
        </listItem>
      </list>
      <para>If your application must use any of these ADO libraries for reasons of backward compatibility, you need to import the appropriate version of the type library. To do this, follow the procedures in the previous section, replacing <legacyItalic>msado15.dll</legacyItalic> by <legacyItalic>msadoXX.tlb</legacyItalic>, where <legacyItalic>XX</legacyItalic> represents the version number you need to import.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>