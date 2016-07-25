---
title: "Cancel Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e41ee6f-5138-4d32-98ac-05e30a2a6fd2
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
# Cancel Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink> method to cancel a command executing on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object if the connection is busy.</para>
    <code>// BeginCancelJ
import com.ms.wfc.data.*;
import java.io.* ;

public class CancelX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      CancelX();
      System.exit(0);
   }

   // CancelX function

   static void CancelX()
   {
      // Define command strings.
      String strCmdChange = "UPDATE titles SET type = 'self_help' "
         + "WHERE type = 'psychology'";
      String strCmdRestore = "UPDATE titles SET type = 'psychology' "
         + "WHERE type = 'self_help'";
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      // Define ADO Objects.
      Connection cnConn1 = null;

      //Declarations.
      boolean booChanged = false;
      BufferedReader in =
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;

      try
      {
         // Open a connection.
         cnConn1 = new Connection();
         cnConn1.open(strCnn);

         // Begin a transaction, then execute a command asynchronously.
         cnConn1.beginTrans();
         cnConn1.execute(strCmdChange,
            AdoEnums.ExecuteOption.ASYNCEXECUTE);

         // do something else for a little while - this could be changed.

         for (int intLoop = 0; intLoop &lt; 10; intLoop++)
         {
            System.out.println(intLoop);
         }

         // If the command has NOT completed, cancel the execute
         // and roll back the transaction. Otherwise, commit the
         // transaction.

         if ((cnConn1.getState() &amp; AdoEnums.ObjectState.EXECUTING) &gt; 0)
         {
            cnConn1.cancel();
            cnConn1.rollbackTrans();
            booChanged = false;
            System.out.println("\nUpdate canceled.");
         }
         else
         {
            cnConn1.commitTrans();
            booChanged = true;
            System.out.println("\nUpdate complete.");
         }

         //If the change was made, restore the data
         // because this is a demonstration.

         if(booChanged )
         {
            cnConn1.execute(strCmdRestore);
            System.out.println("\nData restored.");
         }

         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a connection, check for null pointer first.
         if (cnConn1 != null)
         {
            PrintProviderError(cnConn1);
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

// EndCancelJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel Method</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>