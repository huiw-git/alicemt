---
title: "Status Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d35cb991-2c5b-4d91-bc07-62104242cae7
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
# Status Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property to display which records have been modified in a batch operation before a batch update has occurred.</para>
    <code>// BeginStatusJ
import java.io.*;
import com.ms.wfc.data.*;

public class StatusX
{
   // The main entry point of the application.

   public static void main (String[] args)
   {
      StatusX();
      System.exit(0);
   }
   // StatusX Function

   static void StatusX()
   {
      // Define ADO Objects.
      Recordset rstTitles = null;

      // Declarations.
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"+
                  "Initial Catalog='Pubs';Integrated Security='SSPI';";
      BufferedReader in = 
         new BufferedReader(new InputStreamReader(System.in));

      try
      {
         // Open Recordset for batch update.
         rstTitles = new Recordset();
         rstTitles.setCursorType(AdoEnums.CursorType.KEYSET);
         rstTitles.setLockType(AdoEnums.LockType.BATCHOPTIMISTIC);
         rstTitles.open("Titles", strCnn, AdoEnums.CursorType.KEYSET, 
            AdoEnums.LockType.BATCHOPTIMISTIC, 
            AdoEnums.CommandType.TABLE);

         // Change the type of psychology titles.
         while(!rstTitles.getEOF())
         {
            if(rstTitles.getField("Type").getString().trim().
               equals(new String("psychology")))
               rstTitles.getField("Type").setString("self_help");

            rstTitles.moveNext();
         }

         // Display Title ID and status.
         rstTitles.moveFirst();

         while(!rstTitles.getEOF())
         {
            if(rstTitles.getStatus()==AdoEnums.RecordStatus.MODIFIED)
               System.out.println(rstTitles.getField("title_id").
                  getString() + "-  Modified");
            else
               System.out.println(rstTitles.getField("title_id").
                  getString());
            rstTitles.moveNext();
         }

         // Cancel the update because this is a demonstration.
         rstTitles.cancelBatch();

         System.out.println("Press &lt;Enter&gt; to continue..");
         in.readLine();
      }
      catch(AdoException ae)
      {
         // Notify the user of any errors that result from ADO.

         // As passing a Recordset, check for the null pointer first.
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
   static void PrintProviderError(Connection cnn1)
   {
      // Print Provider Errors from Connection Object.
      // ErrItem is an item object in the Connections Errors Collection.
      com.ms.wfc.data.Error               ErrItem = null;
      long                                 nCount = 0;
      int                                       i = 0;

      nCount = cnn1.getErrors().getCount();

      // If there are any errors in the collection, print them.
      if ( nCount &gt; 0)
      {
         // Collection ranges from 0 to nCount-1.
         for ( i=0;i&lt;nCount; i++)
         {
            ErrItem = cnn1.getErrors().getItem(i);
            System.out.println("\t Error Number: " + ErrItem.getNumber() 
               + "\t" + ErrItem.getDescription());
         }
      }
   }
   // PrintIOError Function
   static void PrintIOError(java.io.IOException je)
   {
      System.out.println("Error: \n");
      System.out.println("\t Source: " + je.getClass() + "\n");
      System.out.println("\t Description: "+ je.getMessage() + "\n");
   }
}
// EndStatusJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status Property (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>