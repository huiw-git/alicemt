---
title: "Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7fd0eebc-99f4-490e-9b62-0b62b1884d6b
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
# Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example triggers an error, traps it, and displays the <legacyLink xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description</legacyLink>, <legacyLink xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext</legacyLink>, <legacyLink xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpFile</legacyLink>, <legacyLink xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError</legacyLink>, <legacyLink xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number</legacyLink>, <legacyLink xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source</legacyLink>, and <legacyLink xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState</legacyLink> properties of the resulting <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object.</para>
    <code>// BeginDescriptionJ
// The WFC class includes the ADO objects.

import com.ms.wfc.data.*;
import java.io.* ;

public class DescriptionX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      DescriptionX();
      System.exit(0);
   }

   // DescriptionX function

   static void DescriptionX()
   {
      // Declarations.
      BufferedReader in = new 
         BufferedReader(new InputStreamReader(System.in));

      // Define ADO Objects.
      Connection cnConn1 = null;

      try
      {
         // Intentionally trigger an error.
         cnConn1 = new Connection();
         cnConn1.open("nothing");
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.
         PrintProviderError(cnConn1);
      }

      try
      {
         System.out.println("\nPress &lt;Enter&gt; key to continue.");
         in.readLine();
      }
      // System read requires this catch.
      catch( java.io.IOException je)
      {
         PrintIOError(je);
      }
  
   }

   // PrintProviderError Function

   static void PrintProviderError( Connection Cnn1 )
   {
      // Print Provider errors from Connection object.
      // ErrItem is an item object in the Connection's Errors collection.
      com.ms.wfc.data.Error  ErrItem = null;
      long nCount = 0;
      int  i      = 0;

      nCount = Cnn1.getErrors().getCount();

      // If there are any errors in the collection, print them.
      if( nCount &gt; 0);
      {
         // Collection ranges from 0 to nCount - 1
         for (i = 0; i&lt; nCount; i++)
         {
            ErrItem = Cnn1.getErrors().getItem(i);
            System.out.println("\t Error number: " + ErrItem.getNumber()
               + "\t" + ErrItem.getDescription() );
         }
      }

   }

   // PrintIOError Function

   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}
// EndDescriptionJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description Property</link>
<link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error Object</link>
<link xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext Property</link>
<link xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpFile Property</link>
<link xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError Property</link>
<link xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number Property</link>
<link xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source Property (ADO Error)</link>
<link xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>