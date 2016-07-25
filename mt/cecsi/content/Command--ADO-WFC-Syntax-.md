---
title: "Command (ADO/WFC Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 39d0aa06-03ac-4c9a-8400-83947756ef99
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
# Command (ADO/WFC Syntax)
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
          <code>public Command()
public Command(String commandtext)</code>
        </content>
      </section>
      <section>
        <title>Methods</title>
        <content>
          <code>public void cancel()
public com.ms.wfc.data.Parameter createParameter(String
    Name, int Type, int Direction, int Size, Object Value)
public Recordset execute()
public Recordset execute(Object[] parameters)
public Recordset execute(Object[] parameters, int options)
public int executeUpdate(Object[] parameters)
public int executeUpdate(Object[] parameters, int options)
public int executeUpdate()</code>
          <para>The <legacyBold>executeUpdate</legacyBold> method is a special case method that calls the underlying ADO <legacyBold>execute</legacyBold> method with certain parameters. The <legacyBold>executeUpdate</legacyBold> method does not support the return of a <legacyBold>Recordset</legacyBold> object, so the <legacyBold>execute</legacyBold> method's <legacyItalic>options</legacyItalic> parameter is modified with <legacyBold>AdoEnums.ExecuteOptions.NORECORDS</legacyBold>. After the <legacyBold>execute</legacyBold> method completes, its updated <legacyItalic>RecordsAffected </legacyItalic>parameter is passed back to the <legacyBold>executeUpdate</legacyBold> method, which is finally returned as an <legacyBold>int</legacyBold>.</para>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public com.ms.wfc.data.Connection getActiveConnection()
public void setActiveConnection(com.ms.wfc.data.Connection con)
public void setActiveConnection(String conString)
public String getCommandText()
public void setCommandText(String command)
public int getCommandTimeout()
public void setCommandTimeout(int timeout)
public int getCommandType()
public void setCommandType(int type)
public String getName()
public void setName(String name)
public boolean getPrepared()
public void setPrepared(boolean prepared)
public int getState()
public com.ms.wfc.data.Parameter getParameter(int n)
public com.ms.wfc.data.Parameter getParameter(String n)
public com.ms.wfc.data.Parameters getParameters()
public AdoProperties getProperties()</code>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>