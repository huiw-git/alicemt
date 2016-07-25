---
title: "OriginalValue and UnderlyingValue Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfe62974-f768-437f-87c5-8106c4e23ad0
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
# OriginalValue and UnderlyingValue Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue</legacyLink> and <legacyLink xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue</legacyLink> properties by displaying a message if a record's underlying data has changed during a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> batch update.</para>
    <code>// BeginOriginalValueJ
import com.ms.wfc.data.*;
import java.io.* ;

public class OriginalValueX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      OriginalValueX();
      System.exit(0);
   }

   // OriginalValueX function

   static void OriginalValueX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstTitles = null;
      Field fldType = null;

      // Declarations.
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));

      try
      {
         // Open a connection.
         cnConn1 = new Connection();
         cnConn1.open(strCnn);

         // Open recordset for batch update.
         rstTitles = new Recordset();
         rstTitles.setActiveConnection(cnConn1);
         rstTitles.setCursorType(AdoEnums.CursorType.KEYSET);
         rstTitles.setLockType(AdoEnums.LockType.BATCHOPTIMISTIC);
         rstTitles.open("Titles",cnConn1,
                     AdoEnums.CursorType.KEYSET,
                     AdoEnums.LockType.BATCHOPTIMISTIC,
                     AdoEnums.CommandType.TABLE);

         // Set field object variable for Type field.
         fldType = rstTitles.getField("type");

         // Change the type of psychology titles.
         while(!rstTitles.getEOF())
         {
            if(rstTitles.getField("type").getString().
               trim().equals("psychology"))
               fldType.setString("self_help");
            rstTitles.moveNext();
         }

         // Similate a change by another user by updating
         // data using a command string.
         cnConn1.execute("UPDATE Titles SET type = 'sociology' "
                        + "WHERE type = 'psychology'");

         // Check for changes.
         rstTitles.moveFirst();

         while(!rstTitles.getEOF())
         {
            String strOriginalValue = 
               fldType.getOriginalValue().toString().trim();
            String strUnderlyingValue = 
               fldType.getUnderlyingValue().toString().trim();
            if(!(strOriginalValue.equals(strUnderlyingValue)))
            {
               System.out.println("Data has changed!" + "\n\n");
               System.out.println("\tTitle ID: "
                  + rstTitles.getField("title_id").getString().trim() + 
                  "\n");
               System.out.println("\tCurrent value: "
                     + fldType.getString()+ "\n");
               System.out.println("\tOriginal value: "
                     + fldType.getOriginalValue().toString()+ "\n");
               System.out.println("\tUnderlying value: "
                     + fldType.getUnderlyingValue().toString()+ "\n");
               System.out.println("\n\nPress &lt;Enter&gt; to continue..");
               in.readLine();
            }
            rstTitles.moveNext();
         }
         // Cancel the update because this is a demonstration.

         rstTitles.cancelBatch();

         // Restore original values.
         cnConn1.execute("UPDATE Titles SET type = 'psychology' "
                     + "WHERE type = 'sociology'");
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstTitles!= null)
         {
            PrintProviderError(rstTitles.getActiveConnection());
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
         if (rstTitles != null)
            if (rstTitles.getState() == 1)
               rstTitles.close();  
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
// EndOriginalValueJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>