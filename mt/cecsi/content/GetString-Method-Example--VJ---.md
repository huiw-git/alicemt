---
title: "GetString Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8260e68-e255-4c0c-9f13-5cca6a9a9c35
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
# GetString Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString</legacyLink> method.</para>
    <para>Assume you are debugging a data access problem and want a quick, simple way of printing the current contents of a small <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <code>// BeginGetStringJ
// The WFC class includes the ADO objects.
import com.ms.wfc.data.*;
import java.io.* ;

public class GetStringX
{
    // The main entry point for the application.

   public static void main (String[] args)
   {
      GetStringX ();
      System.exit(0);
   }

   // GetStringX  function
   static void GetStringX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstAuthors = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
            "Initial Catalog='Pubs';Integrated Security='SSPI';";
      String strOutput;

      try
      {
         // Get the user input for state.
         System.out.println(
            "Enter a state (CA, IN, KS, MD, MI, OR, TN, UT): ");
         String strState = in.readLine().trim();
         String strQuery = 
            "SELECT au_fname, au_lname, address, city FROM Authors " +
                    "WHERE state = '" + strState + "'";

         // Open recordset with data from Authors table.
         cnConn1 = new Connection();
         cnConn1.open(strCnn);
         rstAuthors = new Recordset();
         rstAuthors.open(strQuery,
                cnConn1,
                AdoEnums.CursorType.STATIC,
                AdoEnums.LockType.READONLY,
                AdoEnums.CommandType.TEXT);

         if (rstAuthors.getRecordCount() &gt; 0)
         {
            // Use all defaults: get all rows, TAB column delimiter, 
            // CARRIAGE RETURN
            // row delimiter, empty-string null delimiter.
            strOutput = 
               rstAuthors.getString(AdoEnums.StringFormat.CLIPSTRING,
               rstAuthors.getRecordCount(),
               "\t ",
               "\n",
               "").trim();
            System.out.println("\nState = '" + strState + "'" +
               "\n\n" +
               "Name             Address             City" +
               "\n");
            System.out.println(strOutput);
         }
         else
            System.out.println("\nNo rows found for state = '" +
               strState + "'\n");

         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstAuthors != null)
         {
            PrintProviderError(rstAuthors.getActiveConnection());
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

   // PrintIOError Function

   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}
// EndGetStringJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>