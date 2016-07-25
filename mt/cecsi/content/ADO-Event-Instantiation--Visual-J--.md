---
title: "ADO Event Instantiation: Visual J++"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e22eedae-07d5-4b1b-a447-4151d1a6c098
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
# ADO Event Instantiation: Visual J++
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This short Microsoft® Visual J++® example shows how you can associate your own function with a particular event.</para>
    <code>// BeginEventExampleVJ
import wfc.data.*;
public class MyClass
{
ConnectionEventHandler handler = 
    new ConnectionEventHandler(this,"onConnectComplete");

    public void onConnectComplete(Object sender,ConnectionEvent e)
    {
        if (e.adStatus == AdoEnums.EventStatus.ERRORSOCCURRED) 
            System.out.println("Connection failed");
        else
            System.out.println("Connection completed");
        return;
    }
    
    void main( void )
    {
        Connection conn = new Connection();
    
        conn.addOnConnectComplete(handler);     // Enable event support.
        conn.open("DSN=Pubs");
        conn.close();
        conn.removeOnConnectComplete(handler);  // Disable event support.
    }
}
// EndEventExampleVJ</code>
    <para>First, the class method <legacyItalic>onConnectionComplete</legacyItalic> is associated with the <legacyBold>ConnectionComplete</legacyBold> event by creating a new <legacyBold>ConnectionEventHandler</legacyBold> object and assigning the <legacyItalic>onConnectComplete</legacyItalic> function to the object.</para>
    <para>The <legacyItalic>main</legacyItalic> function then creates a <legacyBold>Connection</legacyBold> object and enables event handling by calling the <legacyBold>addOnConnectComplete</legacyBold> method and passing it the address of the <legacyItalic>handler</legacyItalic> function.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>