---
title: "Execute, Requery, and Clear Methods Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c92cb19-c13b-4bb3-b4cd-75dc8f42057c
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
# Execute, Requery, and Clear Methods Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyBold>Execute</legacyBold> method when run from both a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method to retrieve current data in a recordset, and the <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink> method to clear the contents of the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection. The ExecuteCommand and PrintOutput procedures are required for this procedure to run.</para>
    <code>// BeginExecuteJ
// The WFC class includes the ADO objects.
import com.ms.wfc.data.*;
import java.io.*;

public class ExecuteX
{
   // Main Function

   public static void main (String[] args)
   {
      ExecuteX();
   }

   // ExecuteX Function

   static void ExecuteX()
   {
      // Define string variables.
      String strSQLChange = "UPDATE Titles SET Type = "
            + "'self_help' WHERE Type = 'psychology'";
      String strSQLRestore = "UPDATE Titles SET Type = "
            + "'psychology' WHERE Type = 'self_help'";
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
            + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      // Define ADO objects.
      Connection  cnConn1    = null;
      Command  cmdChange  = null;
      Recordset  rsTitles  = null;

      try
      {
         // Open connection.
         cnConn1 = new Connection ();
         cnConn1.open(strCnn, "", "", AdoEnums.CommandType.UNSPECIFIED);

         // Create command object.
         cmdChange = new Command();
         cmdChange.setActiveConnection (cnConn1);
         cmdChange.setCommandText (strSQLChange);

         // Open recordset with Titles table.
         rsTitles = new Recordset();
         rsTitles.open("Titles", cnConn1,
                    AdoEnums.CursorType.STATIC,
                    AdoEnums.LockType.OPTIMISTIC,
                    AdoEnums.CommandType.TABLE);

         // Print report of original data.
         System.out.println("\n\n\tData in Titles table "
                        + "before executing the query: \n");
         PrintOutput(rsTitles);

         // Clear extraneous errors from the Errors collection.
         cnConn1.getErrors().clear();

         // Call the ExecuteCommand subroutine to
         // execute cmdChange command.
         ExecuteCommand(cmdChange, rsTitles);

         // Print report of new data.
         System.out.println("\n\n\tData in Titles table after "
            + "executing the query: \n");
         PrintOutput(rsTitles);

         // Use the Connection object's execute method to
         // execute SQL statement to restore data.
         cnConn1.execute(strSQLRestore);

         // Print report of restored data.
         System.out.println("\n\n\tData after executing the query "
            + "to restore the original information: \n");
         PrintOutput(rsTitles);
      }  // End Try statement.
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rsTitles != null)
         {
            PrintProviderError(rsTitles.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rsTitles != null)
            if (rsTitles.getState() == 1)
               rsTitles.close();   
         if (cnConn1 != null)
            if (cnConn1.getState() == 1)
               cnConn1.close();
      }
   }

   // ExecuteCommand Function

   static void ExecuteCommand(Command cmdTemp, Recordset rstTemp)
   {
      try
      {
         // CommandText property already set before function was called.
         cmdTemp.setCommandType(AdoEnums.CommandType.TEXT);
         cmdTemp.execute();

         // Retrieve the current data by requerying the recordset.
         rstTemp.requery(AdoEnums.CommandType.UNKNOWN);
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.
         PrintProviderError(rstTemp.getActiveConnection());
      }
   }

   //  PrintOutput Function

   static void PrintOutput(Recordset rstTemp)
   {
      // Declarations.
      BufferedReader in = new 
         BufferedReader(new InputStreamReader(System.in));

      // Ensure at top of recordset.
      rstTemp.moveFirst();

      // If EOF is true, then no data and skip print loop.
      if( rstTemp.getEOF() )
      {
         System.out.println("\tRecordset empty\n");
      }
      else
      {
         // Enumerate Recordset and print data from each.
         while( !(rstTemp.getEOF()) )
         {
            // Convert variant string to convertable string type.
            System.out.println("\t"
               + rstTemp.getFields().getItem("Title").getValue() + " "
               + rstTemp.getFields().getItem("Type").getValue() + "\n");
            rstTemp.moveNext();
         }
      }
      try
      {
         System.out.println("\nPress &lt;Enter&gt; key to continue.");
         in.readLine();
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

   // PrintIOError Function

   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}
// EndExecuteJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
<link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
<link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>