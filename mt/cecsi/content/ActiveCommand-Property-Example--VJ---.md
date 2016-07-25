---
title: "ActiveCommand Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f28637c7-05ab-482d-b1ce-bbfc41228050
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
# ActiveCommand Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand</legacyLink> property.</para>
    <para>A subroutine is given a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object whose <legacyBold>ActiveCommand</legacyBold> property is used to display the command text and parameter that created the <legacyBold>Recordset</legacyBold>.</para>
    <code>// BeginActiveCommandJ
import com.ms.wfc.data.*;
import java.io.* ;

public class ActiveCommandX   
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      ActiveCommandX();
      System.exit(0);
   }

   // ActiveCommandX function

   static void ActiveCommandX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Command cmd = null;
      Recordset rstAuthors = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";
      String strName;

      try
      {
         System.out.println("Enter an author's name (e.g., Ringer): ");
         strName = in.readLine().trim();
         cmd = new Command();
         cmd.setCommandText("SELECT * FROM authors WHERE au_lname = ?");
         cmd.getParameters().append(cmd.createParameter("LastName",
            AdoEnums.DataType.CHAR,
            AdoEnums.ParameterDirection.INPUT, 20, strName));
         cnConn1 = new Connection();
         cnConn1.open(strCnn);
         cmd.setActiveConnection(cnConn1);
         rstAuthors = cmd.execute(null,AdoEnums.CommandType.TEXT);
         ActiveCommandXprint(rstAuthors);
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
         // Cleanup objects before exit.   
         if (cnConn1 != null)
            if (cnConn1.getState() == 1)
               cnConn1.close();
      }
   }

   // ActiveCommandXprint function
   static void ActiveCommandXprint(Recordset rstp)
   {
      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strName;

      try
      {
         strName = rstp.getActiveCommand().getParameters().
            getItem("LastName").getValue().toString();
         System.out.println("\nCommand text = '" +
            rstp.getActiveCommand().getCommandText() + "'");
         System.out.println("Parameter = '" + strName + "'");
         if(rstp.getBOF())
         {
            System.out.println("Name = '" + strName + "', not found.");
         }
         else
         {
            System.out.println("Name = '" +
               rstp.getField("au_fname").getString() + " " + 
               rstp.getField("au_lname").getString() + 
               "', author ID = '" + 
               rstp.getField("au_id").getString() + "'");
         }
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstp != null)
         {
            PrintProviderError(rstp.getActiveConnection());
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

// EndActiveCommandJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>