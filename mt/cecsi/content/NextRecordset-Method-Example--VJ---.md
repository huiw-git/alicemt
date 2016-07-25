---
title: "NextRecordset Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7948eefb-f5cc-4e74-b2f4-39033b46243d
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
# NextRecordset Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink> method to view the data in a recordset that uses a compound command statement made up of three separate <legacyBold>SELECT</legacyBold> statements.</para>
    <code>// BeginNextRecordsetJ
import java.io.*;
import com.ms.wfc.data.*;

public class NextRecordsetX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      NextRecordsetX();
      System.exit(0);
   }
   // NextRecordsetX Function
   static void NextRecordsetX()
   {
      // Define ADO Object
      Recordset rstCompound = null;

      // Declarations
      BufferedReader in = 
         new BufferedReader(new InputStreamReader(System.in));
      String strCnn;
      int intCount;
      int intDisplayRecords = 15;
      int intRecordCount;

      try
      {
         // Open compound recordset.
         strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
             "Initial Catalog='Pubs';Integrated Security='SSPI';";

         rstCompound = new Recordset();
         rstCompound.open("select * from Authors;" +
             "select * from stores;" +
             "select * from jobs", strCnn, AdoEnums.CursorType.FORWARDONLY, 
            AdoEnums.LockType.READONLY,AdoEnums.CommandType.TEXT);

         // Display results from each select statement.
         intCount=1;

         while (rstCompound != null)
         {  
            System.out.println(
               "Contents of recordset #" + intCount + "\n");
            intRecordCount = 0;
         
            while(!rstCompound.getEOF())
               {
                  System.out.println(
                     rstCompound.getField(0).getString()+" " + 
                     rstCompound.getField(1).getString());
                  intRecordCount++;
                  
                  rstCompound.moveNext();
                  if ( intRecordCount == intDisplayRecords)
                  {
                     System.out.println("\nPress &lt;Enter&gt; to continue..");
                     in.readLine();
                     intRecordCount = 0;
                  }
               }
            System.out.println("\nPress &lt;Enter&gt; to continue..");
            in.readLine();

            rstCompound = rstCompound.nextRecordset(); 

            intCount++;
         }
      }
      // System read requires this catch.
      catch(java.io.IOException je)
      {
         PrintIOError(je);
      }
      catch(AdoException ae)
      {
         // Notify the user of any errors that result from ADO.

         // As passing a recordset. check for the null pointer first
         if(rstCompound!=null)
         {
            PrintProviderError(rstCompound.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }
      catch(java.lang.NullPointerException ne)
      {
         System.out.println("Error Description: " + ne.getMessage());
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rstCompound != null)
            if (rstCompound.getState() == 1)
               rstCompound.close();
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
// EndNextRecordsetJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>