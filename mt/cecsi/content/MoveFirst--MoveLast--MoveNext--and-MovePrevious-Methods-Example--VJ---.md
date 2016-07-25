---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d2db8a95-3072-4007-a127-44376405a67e
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
# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveLast</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink>, and <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink> methods to move the record pointer of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the supplied command. The MoveAny procedure is required for this procedure to run.</para>
    <code>// BeginMoveFirstJ
import com.ms.wfc.data.*;
import java.io.*;

public class MoveFirstX  // DLL name.
{
   // Main Function

   public static void main( String rgArg[] )
   {
      MoveFirstX();
   }

   // MoveFirstX Function

   static void MoveFirstX()
   {
      // Declarations
      Recordset rsAuthors = null;
      BufferedReader in = 
            new BufferedReader(new InputStreamReader(System.in));
      String  line = null;

      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      String strMessage = "UPDATE Titles SET type = 'psychology' "
         +"WHERE type = 'self_help'";

      int intCommand = 0;
      String strFName;
      String strLName;

      try
      {
         // Open recordset from Authors table.
         rsAuthors = new Recordset();
         rsAuthors.setCursorLocation( AdoEnums.CursorLocation.CLIENT );

         // Use client cursor to enable AbsolutePosition property.
         rsAuthors.open( "Authors", strCnn, AdoEnums.CursorType.STATIC,
            AdoEnums.LockType.BATCHOPTIMISTIC, AdoEnums.CommandType.TABLE );

         // Get user's move requests and show current record information.
         while( true )   // Continuous loop.
         {
            // Assign field information to variable to simplify output code.
            strFName = rsAuthors.getField("au_fname").getString();
            strLName = rsAuthors.getField("au_lname").getString();

            System.out.println
               ( "\nName: " + strFName + " " + strLName + "\n"
               + "Record " + rsAuthors.getAbsolutePosition()
               + " of " + rsAuthors.getRecordCount() + "\n\n" );
            System.out.println( "[1 - MoveFirst, 2 - MoveLast, \n");
            System.out.println( " 3 - MoveNext, 4 - MovePrevious]\n");

            // User types a number followed by enter (cr-lf).
            line = in.readLine();

            // No entry exits program loop.
            if (line.length() == 0) break;
            // Convert string entry to int.
            intCommand = Integer.parseInt(line);
            // Out of range entry exits program loop.
            if ((intCommand &lt; 1) || (intCommand &gt; 4)) break;

            // Call method based on user's validated selection.
            MoveAny(intCommand, rsAuthors);
         }
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rsAuthors != null)
         {
            PrintProviderError(rsAuthors.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }
      // System Read requires this catch.
      catch( java.io.IOException je )
      {
         PrintIOError(je);
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rsAuthors != null)
            if (rsAuthors.getState() == 1)
               rsAuthors.close();
      }
   }

   // MoveAny Function

   static void MoveAny(int intChoice, Recordset rsTemp)
   {
      // Move per selection from user, checking for BOF and EOF.
      try
      {
         switch(intChoice)
         {
         case 1:   // Equals char of 1.
            rsTemp.moveFirst();
            break;
         case 2:   // Equals char of 2.
            rsTemp.moveLast();
            break;
         case 3:   // Equals char of 3.
            rsTemp.moveNext();
            if(rsTemp.getEOF())
            {
               System.out.println("\nAlready at end of recordset!\n");
               rsTemp.moveLast();
            }
            break;
         case 4:   // Equals char of 4.
            rsTemp.movePrevious();
            if(rsTemp.getBOF())
            {
               System.out.println
                  ("\nAlready at beginning of recordset!\n");
               rsTemp.moveFirst();
            }
            break;
         default:
            break;
         }
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rsTemp != null)
         {
            PrintProviderError(rsTemp.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
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
// EndMoveFirstJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>