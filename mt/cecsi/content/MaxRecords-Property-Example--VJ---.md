---
title: "MaxRecords Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5f12f3b-8f45-4bfa-b70e-971b758e1898
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
# MaxRecords Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords</legacyLink> property to open a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> containing the 10 most expensive titles in the <legacyBold><legacyItalic>Titles</legacyItalic></legacyBold> table.</para>
    <code>// BeingMaxRecordsJ
import java.io.*;
import com.ms.wfc.data.*;

public class MaxRecordsX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      MaxRecordsX();
      System.exit(0);
   }
   // MaxRecordsX Function

   static void MaxRecordsX()
   {
      //  Define ADO Objects
      Recordset rstTemp = null;

      try
      {
         // Declarations
         BufferedReader in = 
            new BufferedReader(new InputStreamReader(System.in));

         // Open recordset containing the 10 most expensive
         // titles in the Titles table.
         String strCnn = " Provider='sqloledb';Data Source='MySqlServer';"+
            " Initial Catalog='Pubs';Integrated Security='SSPI';";
         rstTemp = new Recordset();
         rstTemp.setMaxRecords(10);
         rstTemp.open("select title,price from Titles" + 
            " order by price desc", strCnn,AdoEnums.CursorType.FORWARDONLY, 
            AdoEnums.LockType.READONLY, AdoEnums.CommandType.TEXT);

         // Display the contents of the recordset.
         System.out.println("Top Ten Titles by Price:\n");
         while (!rstTemp.getEOF())
         {
            System.out.println(" "+ rstTemp.getField("title").getString() +
               " - " + rstTemp.getField("Price").getString());
            rstTemp.moveNext();
         }

         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }

      catch(AdoException ae)
      {
         // Notify the user of any errors that result from ADO.

         // As passing a connection, check for null pointer first.
         if (rstTemp!=null)
         {
            PrintProviderError(rstTemp.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getLocalizedMessage());
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
         if (rstTemp != null)
            if (rstTemp.getState() == 1)
               rstTemp.close();
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
// EndMaxRecordsJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>