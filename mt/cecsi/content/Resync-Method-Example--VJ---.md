---
title: "Resync Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ef0ed20-83ac-4047-9294-506fd82f7201
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
# Resync Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates using the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method to refresh data in a static recordset.</para>
    <code>// BeginResyncJ
import java.io.*;
import com.ms.wfc.data.*;

public class ResyncX
{
   // The main entry point of the application.
   public static void main (String[] args)
   {
      ResyncX();
      System.exit(0);
   }
   static void ResyncX()
   {
      // Define ADO Objects.
      Recordset rstTitles = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader(new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
                  "Initial Catalog='Pubs';Integrated Security='SSPI';";

      try
      {
         // Open recordset for Titles table.
         rstTitles = new Recordset();
         rstTitles.setCursorLocation(AdoEnums.CursorLocation.CLIENT);
         rstTitles.setCursorType(AdoEnums.CursorType.STATIC);
         rstTitles.setLockType(AdoEnums.LockType.BATCHOPTIMISTIC);
         rstTitles.open("Titles", strCnn, AdoEnums.CursorType.STATIC, 
            AdoEnums.LockType.BATCHOPTIMISTIC, 
            AdoEnums.CommandType.TABLE);

         // Change the type of the first title in the recordset.
         rstTitles.getField("type").setString("database");

         // Display the results of the change.
         System.out.println("\n\n\tBefore resync:\n" + "\tTitle - " +
            rstTitles.getField("title").getString() +
            "\n\tType  - " + rstTitles.getField("type").getString());

         // Resync with database and redisplay the results.
         rstTitles.resync();
         System.out.println("\n\n\tAfter resync:\n" + "\tTitle - " +
            rstTitles.getField("title").getString() +
            "\n\tType  - " + 
            rstTitles.getField("type").getString()+"\n");
         rstTitles.cancelBatch();

         System.out.println("\tPress &lt;Enter&gt; to continue..");
         in.readLine();

      }
      catch(AdoException ae)
      {
         // Notify user of any errors that result from ADO.

         // As passing a recordset, check for null pointer first.
         if(rstTitles != null)
         {
            PrintProviderError(rstTitles.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }
      // System read requires this catch.
      catch(java.io.IOException je)
      {
         PrintIOError(je);
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rstTitles != null)
            if (rstTitles.getState() == 1)
               rstTitles.close();
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
// EndResyncJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>