---
title: "Optimize Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a75d5239-54a9-4eec-b144-a5848cdbf265
caps.latest.revision: 10
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
# Optimize Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object dynamic <legacyBold>Optimize</legacyBold> property. The <legacyBold><legacyItalic>zip</legacyItalic></legacyBold> field of the <legacyBold>Authors</legacyBold> table in the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database is not indexed. Setting the <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink> property to <languageKeyword>True</languageKeyword> on the <legacyBold><legacyItalic>zip</legacyItalic></legacyBold> field authorizes ADO to build an index that improves the performance of the <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method.</para>
    <code>// BeginOptimizeJ
import com.ms.wfc.data.*;
import java.io.* ;

public class OptimizeX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      OptimizeX();
      System.exit(0);
   }

   // OptimizeX function

   static void OptimizeX()
   {

      // Define ADO Objects.
      Recordset rstAuthors = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      try
      {
         rstAuthors = new Recordset();
         rstAuthors.setCursorLocation(AdoEnums.CursorLocation.CLIENT);
         // Enable index creation.
         rstAuthors.open("SELECT * FROM Authors",
               strCnn,
               AdoEnums.CursorType.STATIC,
               AdoEnums.LockType.READONLY,
               AdoEnums.CommandType.TEXT);
         rstAuthors.getField("zip").getProperties().
            getItem("Optimize").setBoolean(true); // Create the index.
         rstAuthors.find("zip = '94595'");   // Find Akiko Yokomoto.
         System.out.println(rstAuthors.getField("au_fname").getString() + 
            " " + rstAuthors.getField("au_lname").getString() + " " + 
            rstAuthors.getField("address").getString() + " " + 
            rstAuthors.getField("city").getString() + " " + 
            rstAuthors.getField("state").getString() + " ");
         rstAuthors.getField("zip").getProperties().
            getItem("Optimize").setBoolean(false); // Delete the index.

         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstAuthors != null)
         {
            PrintProviderError(rstAuthors.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }

      // System read requires this catch.
      catch( java.io.IOException je)
      {
         PrintIOError(je);
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rstAuthors != null)
            if (rstAuthors.getState() == 1)
               rstAuthors.close();
      }
   }

   // PrintProviderError Function

   static void PrintProviderError( Connection Cnn1 )
   {
      // Print Provider errors from Connection object.
      // ErrItem is an item object in the Connections Errors collection.
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
// EndOptimizeJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize Property—Dynamic (ADO)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>