---
title: "ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69a4a219-8d52-401b-9e92-2ef415f68b05
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
# ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink>, <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink>, <legacyLink xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout</legacyLink>, <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink>, <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink>, and <legacyLink xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction</legacyLink> properties to execute a stored procedure.</para>
    <code>// BeginActiveConnectionJ
import com.ms.wfc.data.*;
import java.io.*;

public class ActiveConnectionX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      ActiveConnectionX();
      System.exit(0);   
   }

   //.ActiveConnectionX function

   static void ActiveConnectionX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Command cmdByRoyalty = null;
      Parameter prmByRoyalty = null;
      Recordset rstByRoyalty = null;
      Recordset rstAuthors = null;

      //Declarations.
      String strCnn;
      String strAuthorID;
      String strFName;
      String strLName;
      int intRoyalty ;
      BufferedReader in = new BufferedReader 
         (new InputStreamReader (System.in));
      String line = null;

      try
      {
         // Open a connection.

         strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
            + "Initial Catalog='Pubs';Integrated Security='SSPI';";
         cnConn1 = new Connection();
         cnConn1.open(strCnn,"","",AdoEnums.CommandType.UNSPECIFIED);

         // Define a command object for stored procedure.
         cmdByRoyalty = new Command();
         cmdByRoyalty.setActiveConnection(cnConn1);
         cmdByRoyalty.setCommandText("byRoyalty");
         cmdByRoyalty.setCommandType(AdoEnums.CommandType.STOREDPROC);
         cmdByRoyalty.setCommandTimeout(15);

         //Define the stored procedure's input parameter.
         System.out.println ("\nEnter Royalty : ");
         line = in.readLine().trim();
         intRoyalty = Integer.parseInt(line);
         prmByRoyalty = new Parameter ();
         prmByRoyalty.setType(AdoEnums.DataType.INTEGER);
         prmByRoyalty.setSize(3);
         prmByRoyalty.setDirection(AdoEnums.ParameterDirection.INPUT);
         prmByRoyalty.setValue(new Integer(intRoyalty));
         cmdByRoyalty.getParameters().append(prmByRoyalty);

         // Create a recordset by executing the command.

         rstByRoyalty = cmdByRoyalty.execute();

         // Open the Authors table to get author names for display.
         rstAuthors = new Recordset ();
         rstAuthors.open("authors",strCnn,
            AdoEnums.CursorType.FORWARDONLY,
            AdoEnums.LockType.READONLY ,AdoEnums.CommandType.TABLE );

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
         System.out.println("\n\nPress &lt;Enter&gt; key to continue.");
         line = in.readLine();

         //Cleanup objects before exit.
         rstByRoyalty.close();
         rstAuthors.close();
         cnConn1.close();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object
         if(rstByRoyalty.getActiveConnection()==null)
            System.out.println("Exception: " + ae.getMessage());
         if(rstAuthors.getActiveConnection()==null)
            System.out.println("Exception: " + ae.getMessage());
         // As passing a Recordset, check for null pointer first.
         if (rstByRoyalty != null)
         {
            PrintProviderError(rstByRoyalty.getActiveConnection());
         }
         if (rstAuthors != null)
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

   //.PrintIOError Function
   
   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}

// EndActiveConnectionJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection Property</link>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout Property</link>
<link xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType Property</link>
<link xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction Property</link>
<link xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>