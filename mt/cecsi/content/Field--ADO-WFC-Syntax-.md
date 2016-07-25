---
title: "Field (ADO/WFC Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 7e01cb24-2338-4f92-ad46-8d97248e1a4d
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
# Field (ADO/WFC Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>package com.ms.wfc.data</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>public void appendChunk(byte[] bytes)
public void appendChunk(char[] chars)
public void appendChunk(String chars)
public byte[] getByteChunk(int len)
public char[] getCharChunk(int len)
public String getStringChunk(int len)</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public int getActualSize()
public int getAttributes()
public void setAttributes(int pl)
public com.ms.com.IUnknown getDataFormat()
public void setDataFormat(com.ms.com.IUnknown format)</code>
          <para>(For more information, see the Microsoft Visual J++ WFC Reference documentation for the com.ms.wfc.data.IDataFormat interface.)</para>
          <code>public int getDefinedSize()
public void setDefinedSize(int pl)
public String getName()
public int getNumericScale()
public void setNumericScale(byte pbNumericScale)
public Variant getOriginalValue()
public int getPrecision()
public void setPrecision(byte pbPrecision)
public int getType()
public void setType(int pDataType)
public Variant getUnderlyingValue()
public Variant getValue()
public void setValue(Variant value)
public AdoProperties getProperties()</code>
        </content>
      </section>
      <section>
        <title>Field Accessor Methods</title>
        <content>
          <para>The <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object gets or sets the content of that object. The content is represented as a VARIANT, a type of object that can be assigned a value and any of several data types.</para>
          <para>ADO/WFC implements the <legacyBold>Value</legacyBold> property with the <legacyBold>getValue</legacyBold> method, which returns a VARIANT object; and the <legacyBold>setValue</legacyBold> method, which takes a VARIANT as an argument. VARIANTs are highly efficient in certain languages, such as Microsoft Visual Basic. However, you can attain better performance in Microsoft Visual J++ by using native Java data types.</para>
          <para>In addition to the <legacyBold>Value</legacyBold> property, ADO/WFC provides <legacyItalic>accessor </legacyItalic>methods that use Java data types to get and set the content of <legacyBold>Field</legacyBold> objects. Most of these methods have names of the form <legacyBold>get</legacyBold><legacyItalic>DataType</legacyItalic> or <legacyBold>set</legacyBold><legacyItalic>DataType</legacyItalic>.</para>
          <para>There are two noteworthy exceptions: One of the <legacyBold>getObject</legacyBold> methods returns an object coerced into a specified class. There is no <legacyBold>getNull</legacyBold> property; instead, there is an <legacyBold>isNull</legacyBold> property that returns a Boolean value indicating whether the field is null.</para>
          <code>public native boolean <codeFeaturedElement>getBoolean</codeFeaturedElement>();
public void <codeFeaturedElement>setBoolean</codeFeaturedElement>(boolean <legacyItalic>v</legacyItalic>)
public native byte <codeFeaturedElement>getByte</codeFeaturedElement>();
public void <codeFeaturedElement>setByte</codeFeaturedElement>(byte <legacyItalic>v</legacyItalic>)
public native byte[] <codeFeaturedElement>getBytes</codeFeaturedElement>();
public void <codeFeaturedElement>setBytes</codeFeaturedElement>(byte[] <legacyItalic>v</legacyItalic>)
public native double <codeFeaturedElement>getDouble</codeFeaturedElement>();
public void <codeFeaturedElement>setDouble</codeFeaturedElement>(double <legacyItalic>v</legacyItalic>)
public native float <codeFeaturedElement>getFloat</codeFeaturedElement>();
public void <codeFeaturedElement>setFloat</codeFeaturedElement>(float <legacyItalic>v</legacyItalic>)
public native int <codeFeaturedElement>getInt</codeFeaturedElement>();
public void <codeFeaturedElement>setInt</codeFeaturedElement>(int <legacyItalic>v</legacyItalic>)
public native long <codeFeaturedElement>getLong</codeFeaturedElement>();
public void <codeFeaturedElement>setLong</codeFeaturedElement>(long <legacyItalic>v</legacyItalic>)
public native short <codeFeaturedElement>getShort</codeFeaturedElement>();
public void <codeFeaturedElement>setShort</codeFeaturedElement>(short <legacyItalic>v</legacyItalic>)
public native String <codeFeaturedElement>getString</codeFeaturedElement>();
public void <codeFeaturedElement>setString</codeFeaturedElement>(String <legacyItalic>v</legacyItalic>)
public native boolean <codeFeaturedElement>isNull</codeFeaturedElement>();
public void <codeFeaturedElement>setNull</codeFeaturedElement>()
public Object <codeFeaturedElement>getObject</codeFeaturedElement>()
public Object <codeFeaturedElement>getObject</codeFeaturedElement>(Class <legacyItalic>c</legacyItalic>)
public void <codeFeaturedElement>setObject</codeFeaturedElement>(Object <legacyItalic>value</legacyItalic>)</code>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>