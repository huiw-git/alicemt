---
title: "Find Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd92d39e-0f7f-4fa6-a9f3-9cd5f00f184d
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
# Find Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method to locate and count the number of business titles in the <legacyBold>Pubs</legacyBold> database. The example assumes the underlying provider does not support similar functionality.</para>
    <code>// BeginFindJ
// The WFC class includes the ADO objects.
import com.ms.wfc.data.*;
import java.io.* ;
import com.ms.com.*;

public class FindX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      FindX();
      System.exit(0);
   }

   // FindX function

   static void FindX()
   {

      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstTitles = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
            "Initial Catalog='Pubs';Integrated Security='SSPI';";
      Variant varMark = null;
      int intCount = 0;

      try
      {
         cnConn1 = new Connection();
         cnConn1.open(strCnn);
         rstTitles = new Recordset();
         rstTitles.open("SELECT title_id FROM titles",
               cnConn1,
               AdoEnums.CursorType.STATIC,
               AdoEnums.LockType.READONLY,
               AdoEnums.CommandType.TEXT);

         //  The default parameters are sufficient to search forward
         //  through a Recordset.
         rstTitles.find("title_id LIKE 'BU%'");

         // Skip current record to avoid finding the same row repeatedly.
         // The bookmark is redundant because Find searches from current
         // position.
         while(!rstTitles.getEOF()) // Continue if last find succeeded.
         {
            System.out.println("Title ID: "
                           + rstTitles.getField("title_id").getString());
            intCount++; // Count the last title found.
            varMark = (Variant)rstTitles.getBookmark(); 
            // Note current position.
            rstTitles.find("title_id LIKE 'BU%'",
                   1,
                   AdoEnums.SearchDirection.FORWARD,
                   varMark);
         }

         System.out.println("\nThe number of business titles is " +
                        Integer.toString(intCount));
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstTitles != null)
         {
            PrintProviderError(rstTitles.getActiveConnection());
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
         if (rstTitles != null)
            if (rstTitles.getState() == 1)
               rstTitles.close();  
         if (cnConn1 != null)
            if (cnConn1.getState() == 1)
               cnConn1.close();
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
// EndFindJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>