---
title: "Count Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68cc1395-2433-4000-98dc-9e860170cd59
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
# Count Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property with two collections in the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> database. The property obtains the number of objects in each collection, and sets the upper limit for loops that enumerate these collections. Another way to enumerate these collections without using the <legacyBold>Count</legacyBold> property would be to use <codeInline>For Each...Next</codeInline> statements.</para>
    <code>// BeginCountJ
import com.ms.wfc.data.*;
import java.io.* ;

public class CountX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      CountX();
      System.exit(0);
   }

   // CountX function

   static void CountX()
   {

      // Define ADO Objects.
      Recordset rstEmployees = null;

      // Declarations.
      BufferedReader in =
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      int intLoop;
      int intDisplaySize = 20;
      int recCount=0;

      try
      {
         rstEmployees = new Recordset();

         // Open recordset with data from Employees table.
         rstEmployees.open("employee", strCnn,
            AdoEnums.CursorType.FORWARDONLY,
            AdoEnums.LockType.READONLY,
            AdoEnums.CommandType.TABLE);

         // Print information about Fields collection.
         System.out.println(rstEmployees.getFields().getCount() +
            " Fields in Employees");
         for ( intLoop = 0; intLoop &lt;
            rstEmployees.getFields().getCount(); intLoop++)
         {
            System.out.println("\t" +
               rstEmployees.getFields().getItem(intLoop).getName());
         }
         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();

         // Print information about Properties collection.
         System.out.println(rstEmployees.getProperties().getCount() +
            " Properties in Employees");
         for ( intLoop = 0; intLoop &lt;
            rstEmployees.getProperties().getCount(); intLoop++)
         {
            System.out.println("\t" +
               rstEmployees.getProperties().getItem(intLoop).getName());
            recCount++;
            if ( recCount &gt;= intDisplaySize)
            {
               System.out.println("\n\nPress &lt;Enter&gt; to continue..");
               in.readLine();
               recCount = 0;
            }
         }
         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if (rstEmployees.getActiveConnection()==null)
         {
            System.out.println("Exception: " + ae.getMessage());
         }
         else
         {
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

   // PrintIOError Function

   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}

// EndCountJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>