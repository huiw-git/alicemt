---
title: "Clone Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b699f2b-e5c7-4584-ab25-663a9243d30e
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
# Clone Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink> method to create copies of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and then lets the user position the record pointer of each copy independently.</para>
    <code>// BeginCloneJ
import com.ms.wfc.data.*;
import java.io.* ;

public class CloneX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      CloneX();
      System.exit(0);
   }

   // CloneX function

   static void CloneX()
   {
      // Assign SQL statement and connection string to variables.
      String strSQL = "SELECT stor_name FROM Stores "
         + "ORDER BY stor_name";

      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      // Define ADO Objects.
      Recordset[] arstStores = null;

      //Declarations.
      BufferedReader in =
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strMessage;
      String strFind;
      int  intLoop;
      boolean booExit = true;

      try
      {
         // Open recordset as a static cursor type recordset.
         arstStores = new Recordset[3];
         arstStores[0] = new Recordset();
         arstStores[0].setCursorType(AdoEnums.CursorType.STATIC);
         arstStores[0].setLockType(AdoEnums.LockType.BATCHOPTIMISTIC);
         arstStores[0].open(strSQL,strCnn,AdoEnums.CursorType.STATIC,
            AdoEnums.LockType.BATCHOPTIMISTIC,AdoEnums.CommandType.TEXT);

         // Create two clones of the original Recordset.
         arstStores[1] = (Recordset)arstStores[0].clone
            (AdoEnums.LockType.BATCHOPTIMISTIC);
         arstStores[2] = (Recordset)arstStores[0].clone
            (AdoEnums.LockType.BATCHOPTIMISTIC);

         while(booExit)
         {
            // Loop through the array so that on each pass,
            // the user is searching a different copy of the
            // same Recordset.
            for (intLoop = 0; intLoop &lt; 3; intLoop++)
            {
               // Ask for search string while showing where
               // the current record pointer is for each Recordset
               strMessage = "\nRecordsets from stores table:" + "\n"
                  +  "  1 - Original - Record pointer at "
                  + arstStores[0].getField("stor_name").getString()
                  + "\n" + "  2 - Clone - Record pointer at "
                  + arstStores[1].getField("stor_name").getString()
                  + "\n" + "  3 - Clone - Record pointer at "
                  + arstStores[2].getField("stor_name").getString()
                  + "\n";
               System.out.println(strMessage);
               System.out.println("Enter search string for #"
                  + (intLoop+1) + "(Press &lt;Enter&gt; to Exit.)");

               strFind = in.readLine().trim();
               if(strFind.length() == 0)
               {
                  booExit = false;
                  break;
               }

               // Find the search string; if there's no
               // match, jump to the last record.
               arstStores[intLoop].setFilter("stor_name &gt;= '" +
                  strFind + "'");
               if (arstStores[intLoop].getEOF())
               {
                  arstStores[intLoop].setFilter
                     (new Integer(AdoEnums.FilterGroup.NONE));
                  arstStores[intLoop].moveLast();
               }
            }
         }
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a connection, check for null pointer first.
         if (arstStores[0] != null)
         {
            PrintProviderError(arstStores[0].getActiveConnection());
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
         if (arstStores[0] != null)
            if (arstStores[0].getState() == 1)
               arstStores[0].close();  
         if (arstStores[1] != null)
            if (arstStores[1].getState() == 1)
               arstStores[1].close();  
         if (arstStores[2] != null)
            if (arstStores[2].getState() == 1)
               arstStores[2].close();
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
// EndCloneJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>