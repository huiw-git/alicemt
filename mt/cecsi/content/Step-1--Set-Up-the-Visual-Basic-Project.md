---
title: "Step 1: Set Up the Visual Basic Project"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
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
# Step 1: Set Up the Visual Basic Project
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In this scenario, it is assumed that you have Microsoft Visual Basic 6.0, ADO 2.5 or later, and the Microsoft OLE DB Provider for Internet Publishing installed on your system. You will first create a new project, and then add some controls to the default form in the project.</para>
    <procedure>
      <title>To create an ADO project:</title>
      <steps class="ordered">
        <step>
          <content>
            <para>In Microsoft Visual Basic, create a new Standard EXE project.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the Project menu, choose References.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select "Microsoft ActiveX Data Objects 2.5 Library" and click OK.</para>
          </content>
        </step>
      </steps>
    </procedure>
    <procedure>
      <title>To insert controls on the main form:</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Add a ListBox control to Form1. Set its Name property to <userInputLocalizable>lstMain</userInputLocalizable>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Add another ListBox control to Form1. Set its Name property to <userInputLocalizable>lstDetails</userInputLocalizable>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Add a TextBox control to Form1. Set its Name property to <userInputLocalizable>txtDetails</userInputLocalizable>.</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics>
<link xlink:href="2f551969-0fd9-41ee-b81d-100975a4bdc2">Internet Publishing Scenario</link>
<link xlink:href="a1454493-1c86-46c2-ada8-d3c6fcdaf3c1">Step 2: Initialize the Main List Box</link>
</relatedTopics>
</developerConceptualDocument>