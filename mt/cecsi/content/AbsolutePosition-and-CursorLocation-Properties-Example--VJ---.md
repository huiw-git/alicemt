---
title: "AbsolutePosition and CursorLocation Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74afb37a-92b5-4cab-be49-18fb866e4d53
caps.latest.revision: 10
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
# AbsolutePosition and CursorLocation Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink> property can track the progress of a loop that enumerates all the records of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. It uses the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to enable the <legacyBold>AbsolutePosition</legacyBold> property by setting the cursor to a client cursor.</para>
    <code>// BeginAboslutePositionJ
import com.ms.wfc.data.*;
import java.io.*;

public class AbsolutePositionX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      AbsolutePositionX();
      System.exit(0);
   }

   //.AbsolutePositionX function

   static void AbsolutePositionX()
   {

      // define ADO Objects.
      Recordset rstEmployees = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader(new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
         "Initial Catalog='Pubs';Integrated Security='SSPI';";

      String strLName;
      String strMessage;
      String strAbsolutePosition,strRecordCount;
      int intAbsolutePosition;
      int intRecordCount;
      int intChoice;
      
      try
      {

         rstEmployees = new Recordset();

         // Use client cursor to enable AbsolutePosition property.
         rstEmployees.setCursorLocation( AdoEnums.CursorLocation.CLIENT);

         // Open a recordset for Employees table using a client cursor.
         rstEmployees.open("employee", strCnn,
            AdoEnums.CursorType.FORWARDONLY ,
            AdoEnums.LockType.READONLY,
            AdoEnums.CommandType.TABLE);

         // Enumerate Recordset.
         while ( !rstEmployees.getEOF()) // continuous loop
         {
            intRecordCount = rstEmployees.getRecordCount();
            strRecordCount = Integer.toString(intRecordCount);

            // Read data field in the variables.
            strLName = rstEmployees.getField("lname").getString();
            intAbsolutePosition = rstEmployees.getAbsolutePosition();
            strAbsolutePosition = Integer.toString(intAbsolutePosition);

            // Display current record information.
            strMessage = "\nEmployee: " + strLName + "\n" + "(Record " + 
               strAbsolutePosition + " of " +strRecordCount + " )";
            System.out.println(strMessage);
            System.out.println(
               "\nDo you want to continue (1 -&gt; Yes / 2 -&gt; No)?");
            //user types a number followed by enter (cr-lf).
            line = in.readLine().trim();
            intChoice = Integer.parseInt(line);
            if ( intChoice != 1)
               break;
            rstEmployees.moveNext();
         }
      }

      catch( NumberFormatException ne)
      {
         System.out.println("\nException : Integer Input required.");
         System.exit(0);
      }

      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if (rstEmployees.getActiveConnection()== null)
            System.out.println("Exception: " + ae.getMessage());
         // As passing a Recordset, check for null pointer first.
         if (rstEmployees != null)
         {
            PrintProviderError(rstEmployees.getActiveConnection());
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
         if (rstEmployees != null)
            if (rstEmployees.getState() == 1)
               rstEmployees.close();
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

// EndAbsolutePositionJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition Property</link>
<link xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>