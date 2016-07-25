---
title: "Filter and RecordCount Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16d5d896-9905-4f75-973b-e1e696cd169f
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
# Filter and RecordCount Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property to open a new <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on a specified condition applied to an existing <legacyBold>Recordset</legacyBold>. It uses the <legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink> property to show the number of records in the two <legacyBold>Recordsets</legacyBold>. The FilterField function is required for this procedure to run.</para>
    <code>// BeginFilterJ
// The WFC class includes the ADO objects.

import com.ms.wfc.data.*;
import java.io.* ;

public class FilterX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      FilterX();
      FilterX2();
      System.exit(0);
   }

   // FilterX function
   static void FilterX()
   {

      // Define ADO Objects.
      Recordset rstPublishers = null;
      Recordset rstPublishersCountry = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
            + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      int intPublisherCount;
      String strCountry;
      String strMessage;

      try
      {
         rstPublishers = new Recordset();

         // Open recordset with data from Publishers table.
         rstPublishers.setCursorType(AdoEnums.CursorType.STATIC);
         rstPublishers.open("publishers", strCnn,
                    AdoEnums.CursorType.STATIC,
                    AdoEnums.LockType.READONLY,
                    AdoEnums.CommandType.TABLE);

         // Populate the Recordset.
         intPublisherCount = rstPublishers.getRecordCount();

         // Get user input.
         System.out.println("Enter a country to filter on:");
         strCountry = in.readLine().trim();

         if(!strCountry.equals(""))
         {
            // Open a filtered Recordset object.
            rstPublishersCountry = 
               FilterField(rstPublishers, "Country", strCountry);
            if(rstPublishersCountry.getRecordCount()==0)
               System.out.println("\nNo publishers from that country.");
            else
            {
               // Print number of records for the original
               // Recordset object and the filtered Recordset
               // object.
               strMessage = "\nOrders in original recordset: " + "\n"
                  + intPublisherCount + "\n"
                  + "Orders in filtered recordset (Country = '"
                  + strCountry + "'): \n" 
                  + rstPublishersCountry.getRecordCount();
               System.out.println(strMessage);
            }
            rstPublishersCountry.close();
         }
         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstPublishers != null)
         {
            PrintProviderError(rstPublishers.getActiveConnection());
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
         if (rstPublishers != null)
            if (rstPublishers.getState() == 1)
               rstPublishers.close();
      }

   }

   // FilterField Function

   static Recordset FilterField(Recordset rstTemp,String strField,
                         String strFilter)
   {
      // Set a filter on the specified Recordset object and then
      // open a new Recordset object.
      rstTemp.setFilter(strField + " = '" + strFilter + "'");
      return rstTemp;
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

   // FilterX2 function

   static void FilterX2()
   {

      // Define ADO Objects.
      Recordset rstPublishers = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
            + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      try
      {
         rstPublishers = new Recordset();

         // Open recordset with data from Publishers table.
         rstPublishers.setCursorType(AdoEnums.CursorType.STATIC);
         rstPublishers.open("SELECT * FROM publishers " +
                        "WHERE Country = 'USA'", strCnn,
                        AdoEnums.CursorType.STATIC,
                        AdoEnums.LockType.READONLY,
                        AdoEnums.CommandType.TEXT);

         // Print current data in recordset.
         rstPublishers.moveFirst();
         while(!rstPublishers.getEOF())
         {
            System.out.println(rstPublishers.getField("pub_name").getString()
                        +", "
                        + rstPublishers.getField("country").getString());
            rstPublishers.moveNext();
         }
         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();

         // Cleanup objects before exit.
         rstPublishers.close();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if (rstPublishers.getActiveConnection()==null)
         {
               System.out.println("Exception: " + ae.getMessage());
         }
         else
         {
            // As passing a Recordset, check for null pointer first.
            if (rstPublishers != null)
            {
               PrintProviderError(rstPublishers.getActiveConnection());
            }
            else
            {
               System.out.println("Exception: " + ae.getMessage());
            }
         }
      }

      // System read requires this catch.
      catch( java.io.IOException je)
      {
         PrintIOError(je);
      }

   }
}
// EndFilterJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter Property</link>
<link xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>