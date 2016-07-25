---
title: "CacheSize Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6fe482a-6951-438b-be58-e08f64efd1e2
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
# CacheSize Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property to show the difference in performance for an operation performed with and without a 30-record cache.</para>
    <code>// BeginCacheSizeJ
import com.ms.wfc.data.*;
import java.io.* ;

public class CacheSizeX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      CacheSizeX();
      System.exit(0);
   }

   // CacheSizeX function

   static void CacheSizeX()
   {

      // Define ADO Objects.
      Recordset rstRoySched = null;

      // Declarations.
      BufferedReader in =
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      long timeStart;
      long timeEnd;
      float timeNoCache;
      float timeCache;
      int   intLoop;
      String strTemp;

      try
      {
         // Open the RoySched table.
         rstRoySched = new Recordset();
         rstRoySched.open("roysched", strCnn,
            AdoEnums.CursorType.FORWARDONLY,
            AdoEnums.LockType.READONLY,
            AdoEnums.CommandType.TABLE);

         // Enumerate the Recordset object twice and record
         // the elapsed time.

         timeStart = System.currentTimeMillis();
         for ( intLoop = 0; intLoop &lt; 2; intLoop++)
         {
            rstRoySched.moveFirst();
            while (!rstRoySched.getEOF())
            {
               // Execute a simple operation for the
               // performance test.
               strTemp = rstRoySched.getField("title_id").getString();
               rstRoySched.moveNext();
            }

         }

         timeEnd = System.currentTimeMillis();
         timeNoCache =(float)(timeEnd - timeStart)/1000f;

         // Cache records in groups of 30 records.
         rstRoySched.moveFirst();
         rstRoySched.setCacheSize(30);
         timeStart = System.currentTimeMillis();

         // Enumerate the Recordset object twice and record
         // the elapsed time.
         for ( intLoop = 0; intLoop &lt; 2; intLoop++)
         {
            rstRoySched.moveFirst();
            while (!rstRoySched.getEOF())
            {
               // Execute a simple operation for the
               // performance test.

               strTemp = rstRoySched.getField("title_id").getString();
               rstRoySched.moveNext();
            }

         }

         timeEnd = System.currentTimeMillis();
         timeCache = (float)(timeEnd - timeStart)/1000f;

         // Display performance results.
         System.out.println("\nCaching Performance Results:");
         System.out.println("\n\tNo Cache: " + timeNoCache + " seconds");
         System.out.println("\n\t30-record cache: " + timeCache +
            " seconds");
         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if (rstRoySched.getActiveConnection()==null)
            System.out.println("Exception: " + ae.getMessage());

         // As passing a Recordset, check for null pointer first.
         if (rstRoySched != null)
         {
            PrintProviderError(rstRoySched.getActiveConnection());
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
         if (rstRoySched != null)
            if (rstRoySched.getState() == 1)
               rstRoySched.close();
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

// EndCacheSizeJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>