---
title: "Parameter (ADO/WFC Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
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
# Parameter (ADO/WFC Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>package com.ms.wfc.data</title>
    <content />
    <sections>
      <section>
        <title>Constructor</title>
        <content>
          <code>public Parameter()
public Parameter(String name)
public Parameter(String name, int type)
public Parameter(String name, int type, int dir)
public Parameter(String name, int type, int dir, int size)
public Parameter(String name, int type, int dir, int size, Object value)</code>
        </content>
      </section>
      <section>
        <title>Methods</title>
        <content>
          <code>public void appendChunk(byte[] bytes)
public void appendChunk(char[] chars)
public void appendChunk(String chars)</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public int getAttributes()
public void setAttributes(int attr)
public int getDirection()
public void setDirection(int dir)
public String getName()
public void setName(String name)
public int getNumericScale()
public void setNumericScale(int scale)
public int getPrecision()
public void setPrecision(int prec)
public int getSize()
public void setSize(int size)
public int getType()
public void setType(int type)
public com.ms.com.Variant getValue()
public void setValue(Object v)
public AdoProperties getProperties()</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Parameter Accessor Methods</title>
    <content>
      <para>The <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property of a <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object gets or sets the content of that object. The content is represented as a VARIANT, a type of object that can be assigned a value and any of several data types.</para>
      <para>ADO/WFC implements the <legacyBold>Value</legacyBold> property with the <legacyBold>getValue</legacyBold> method, which returns a VARIANT object; and the <legacyBold>setValue</legacyBold> method, which takes a VARIANT as an argument. VARIANTs are highly efficient in certain languages, such as Microsoft Visual Basic. However, you can attain better performance in Microsoft Visual J++ by using native Java data types.</para>
      <para>In addition to the <legacyBold>Value</legacyBold> property, ADO/WFC provides <legacyItalic>accessor </legacyItalic>methods that use Java data types to get and set the content of <legacyBold>Parameter</legacyBold> objects. Most of these methods have names of the form <legacyBold>get</legacyBold><legacyItalic>DataType</legacyItalic> or <legacyBold>set</legacyBold><legacyItalic>DataType</legacyItalic>.</para>
      <para>There is one noteworthy exception: There is no <legacyBold>getNull</legacyBold> property; instead, there is an <legacyBold>isNull</legacyBold> property that returns a Boolean value indicating whether the field is null.</para>
      <code>public boolean <codeFeaturedElement>getBoolean</codeFeaturedElement>()
public void <codeFeaturedElement>setBoolean</codeFeaturedElement>(boolean <legacyItalic>v</legacyItalic>)
public byte <codeFeaturedElement>getByte</codeFeaturedElement>()
public void <codeFeaturedElement>setByte</codeFeaturedElement>(byte <legacyItalic>v</legacyItalic>)
public double <codeFeaturedElement>getDouble</codeFeaturedElement>()
public void <codeFeaturedElement>setDouble</codeFeaturedElement>(double <legacyItalic>v</legacyItalic>)
public float <codeFeaturedElement>getFloat</codeFeaturedElement>()
public void <codeFeaturedElement>setFloat</codeFeaturedElement>(float <legacyItalic>v</legacyItalic>)
public int <codeFeaturedElement>getInt</codeFeaturedElement>()
public void <codeFeaturedElement>setInt</codeFeaturedElement>(int <legacyItalic>v</legacyItalic>)
public long <codeFeaturedElement>getLong</codeFeaturedElement>()
public void <codeFeaturedElement>setLong</codeFeaturedElement>(long <legacyItalic>v</legacyItalic>)
public short <codeFeaturedElement>getShort</codeFeaturedElement>()
public void <codeFeaturedElement>setShort</codeFeaturedElement>(short <legacyItalic>v</legacyItalic>)
public String <codeFeaturedElement>getString</codeFeaturedElement>()
public void <codeFeaturedElement>setString</codeFeaturedElement>(String <legacyItalic>v</legacyItalic>)
public boolean <codeFeaturedElement>isNull</codeFeaturedElement>()
public void <codeFeaturedElement>setNull</codeFeaturedElement>()</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>