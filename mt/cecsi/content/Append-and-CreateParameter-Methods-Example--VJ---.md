---
title: "Append and CreateParameter Methods Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9673f232-fa58-4439-995a-b4066db628aa
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
# Append and CreateParameter Methods Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> and <legacyLink xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter</legacyLink> methods to execute a stored procedure with an input parameter.</para>
    <code>// BeginAppendJ
import com.ms.wfc.data.*;
import java.io.*;
import com.ms.com.*;

public class AppendX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      AppendX();
   }

   // AppendX function

   static void AppendX()
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
      BufferedReader in = 
         new BufferedReader (new InputStreamReader (System.in));
      String line = null;
      Variant varRoyalty;

      try
      {
         // Open a connection.

         strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
            + "Initial Catalog='Pubs';Integrated Security='SSPI';";
         cnConn1 = new Connection();
         cnConn1.open(strCnn);
         cnConn1.setCursorLocation(AdoEnums.CursorLocation.CLIENT);

         // Open command object with one parameter.
         cmdByRoyalty = new Command();
         cmdByRoyalty.setCommandText("byRoyalty");
         cmdByRoyalty.setCommandType(AdoEnums.CommandType.STOREDPROC);

         //Get parameter value and append parameter.
         System.out.println ("\nEnter Royalty : ");
         line = in.readLine().trim();
         intRoyalty = Integer.parseInt(line);
         varRoyalty = new Variant(intRoyalty);
         prmByRoyalty = cmdByRoyalty.createParameter ("percentage",
            AdoEnums.DataType.INTEGER,
            AdoEnums.ParameterDirection.INPUT,4,varRoyalty);

         cmdByRoyalty.getParameters().append(prmByRoyalty);
         prmByRoyalty.setValue(varRoyalty);

         // Create a recordset by executing the command.
         cmdByRoyalty.setActiveConnection(cnConn1);
         rstByRoyalty = cmdByRoyalty.execute();

         // Open the Authors table to get author names for display.
         rstAuthors = new Recordset ();
         rstAuthors.open("authors", cnConn1, 
            AdoEnums.CursorType.FORWARDONLY,
            AdoEnums.LockType.READONLY, 
            AdoEnums.CommandType.TABLE );

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

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if(rstByRoyalty.getActiveConnection()==null)
            System.out.println("Exception: " + ae.getMessage());
         // As passing a Recordset, check for null pointer first.
         if (rstByRoyalty != null)
         {
            PrintProviderError(rstByRoyalty.getActiveConnection());
         }
         if (rstAuthors != null)
         {
            if (rstAuthors.getActiveConnection()==null)
               System.out.println("Exception: " + ae.getMessage());
            else
               PrintProviderError(rstAuthors.getActiveConnection());
         }
         else 
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }

      // This catch is required if input string cannot be converted to
      // Integer data type.
      catch( java.lang.NumberFormatException ne)
      {
         System.out.println("\nException: Integer Number required.");
         System.exit(0);
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
         System.exit(0);//required here only.
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

// EndAppendJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
<link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>