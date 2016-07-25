---
title: "Refresh Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0fbf728-0ccb-468d-be1e-c09dad9ffddb
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
# Refresh Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates using the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method to refresh the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection for a stored procedure <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
    <code>// BeginRefreshJ
import  com.ms.wfc.data.*;
import java.io.*;

public class RefreshX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      RefreshX();
      System.exit(0);
   }

   // RefreshX function

   static void RefreshX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Command cmdByRoyalty = null;
      Recordset rstByRoyalty = null;
      Recordset rstAuthors = null;

      //Declarations.
      String strAuthorID;
      String strFName;
      String strLName;
      int intRoyalty ;
      BufferedReader in = 
         new BufferedReader (new InputStreamReader (System.in));
      String line = null;

      try
      {
         // Open a connection.
         String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
                     + "Initial Catalog='Pubs';Integrated Security='SSPI';";

         cnConn1 = new Connection();
         cnConn1.open(strCnn);

         // Open a command object for a stored procedure
         // with one parameter.
         cmdByRoyalty = new Command();
         cmdByRoyalty.setActiveConnection(cnConn1);
         cmdByRoyalty.setCommandText("byRoyalty");
         cmdByRoyalty.setCommandType(AdoEnums.CommandType.STOREDPROC);
         cmdByRoyalty.getParameters().refresh();

         // Get Parameter value and execute the command
         // storing the results in the recordset.
         System.out.println ("\nEnter Royalty : ");
         line = in.readLine().trim();
         intRoyalty = Integer.parseInt(line);
         cmdByRoyalty.getParameters().getItem(1).setInt(intRoyalty);

         // Create a recordset by executing the command.
         rstByRoyalty = cmdByRoyalty.execute();

         // Open the Authors table to get author names for display.
         rstAuthors = new Recordset ();
         rstAuthors.open(
            "Authors",strCnn,AdoEnums.CursorType.FORWARDONLY, 
            AdoEnums.LockType.READONLY, AdoEnums.CommandType.TABLE );

         // Print current data in the recordset,
         // adding author names from Authors table.
         System.out.println("\nAuthors with " + intRoyalty +
                        " percent royalty");
         while (!rstByRoyalty.getEOF())
         {
            strAuthorID =  rstByRoyalty.getField("au_id").getString();
            rstAuthors.setFilter("au_id ='" +  strAuthorID + "'");
            strFName = rstAuthors.getField("au_fname").getString();
            strLName = rstAuthors.getField("au_lname").getString();
            System.out.println("\t" + strAuthorID + ", " + strFName
                           + " " + strLName);
            rstByRoyalty.moveNext();
         }
         System.out.println("\n\nPress &lt;Enter&gt; key to continue..");
         line = in.readLine();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstByRoyalty != null)
         {
            PrintProviderError(rstByRoyalty.getActiveConnection());
         }
         else if (rstAuthors != null)
         {
            PrintProviderError(rstAuthors.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }

      // This catch is required if input string cannot be converted to
      // Integer data type.
      catch ( java.lang.NumberFormatException ne)
      {
            System.out.println("\nException: Integer Input required.");
      }
      // System Read requires this catch.
      catch( java.io.IOException je )
      {
         PrintIOError(je);
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rstByRoyalty != null)
            if (rstByRoyalty.getState() == 1)
               rstByRoyalty.close();  
         if (rstAuthors != null)
            if (rstAuthors.getState() == 1)
               rstAuthors.close();  
         if (cnConn1 != null)
            if (cnConn1.getState() == 1)
               cnConn1.close();
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
// EndRefreshJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>