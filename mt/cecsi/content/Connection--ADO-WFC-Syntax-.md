---
title: "Connection (ADO/WFC Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8cfc35bb-91e2-47da-ad4c-982e9162cd51
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
# Connection (ADO/WFC Syntax)
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
          <code>public Connection()
public Connection(String connectionstring)</code>
        </content>
      </section>
      <section>
        <title>Methods</title>
        <content>
          <code>public int beginTrans()
public void commitTrans()
public void rollbackTrans()
public void cancel()
public void close()
public com.ms.wfc.data.Recordset execute(String commandText)
public com.ms.wfc.data.Recordset execute(String commandText, int options)
public int executeUpdate(String commandText)
public int executeUpdate(String commandText, int options)</code>
          <para>The <legacyBold>executeUpdate</legacyBold> method is a special case method that calls the underlying ADO <legacyBold>execute</legacyBold> method with certain parameters. The <legacyBold>executeUpdate</legacyBold> method does not support the return of a <legacyBold>Recordset</legacyBold> object, so the <legacyBold>execute</legacyBold> method's <legacyItalic>options</legacyItalic> parameter is modified with <legacyBold>AdoEnums.ExecuteOptions.NORECORDS</legacyBold>. After the <legacyBold>execute</legacyBold> method completes, its updated <legacyItalic>RecordsAffected </legacyItalic>parameter is passed back to the <legacyBold>executeUpdate</legacyBold> method, which is finally returned as an <legacyBold>int</legacyBold>.</para>
          <code>public void open() 
public void open(String connectionString)
public void open(String connectionString, String userID)
public void open(String connectionString, String userID, String password)
public void open(String connectionString, String userID, String password, int options)
public Recordset openSchema(int schema, Object[]
    restrictions, String schemaID)
public Recordset openSchema(int schema)
public Recordset openSchema(int schema, Object[] restrictions)</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public int getAttributes()
public void setAttributes(int attr)
public int getCommandTimeout()
public void setCommandTimeout(int timeout)
public String getConnectionString()
public void setConnectionString(String con)
public int getConnectionTimeout()
public void setConnectionTimeout(int timeout)
public int getCursorLocation()
public void setCursorLocation(int cursorLoc)
public String getDefaultDatabase()
public void setDefaultDatabase(String db)
public int getIsolationLevel()
public void setIsolationLevel(int level)
public int getMode()
public void setMode(int mode)
public String getProvider()
public void setProvider(String provider)
public int getState()
public String getVersion()
public AdoProperties getProperties()
public com.ms.wfc.data.Errors getErrors()</code>
        </content>
      </section>
      <section>
        <title>Events</title>
        <content>
          <para>For more information about ADO/WFC events, see <legacyLink xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</legacyLink>.</para>
          <code>public void addOnBeginTransComplete(ConnectionEventHandler handler)
public void removeOnBeginTransComplete(ConnectionEventHandler handler)
public void addOnCommitTransComplete(ConnectionEventHandler handler)
public void removeOnCommitTransComplete(ConnectionEventHandler handler)
public void addOnConnectComplete(ConnectionEventHandler handler)
public void removeOnConnectComplete(ConnectionEventHandler handler)
public void addOnDisconnect(ConnectionEventHandler handler)
public void removeOnDisconnect(ConnectionEventHandler handler)
public void addOnExecuteComplete(ConnectionEventHandler handler)
public void removeOnExecuteComplete(ConnectionEventHandler handler)
public void addOnInfoMessage(ConnectionEventHandler handler)
public void removeOnInfoMessage(ConnectionEventHandler handler)
public void addOnRollbackTransComplete(ConnectionEventHandler handler)
public void removeOnRollbackTransComplete(ConnectionEventHandler handler)
public void addOnWillConnect(ConnectionEventHandler handler)
public void removeOnWillConnect(ConnectionEventHandler handler)
public void addOnWillExecute(ConnectionEventHandler handler)
public void removeOnWillExecute(ConnectionEventHandler handler)</code>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>