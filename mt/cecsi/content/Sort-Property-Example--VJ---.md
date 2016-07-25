---
title: "Sort Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 460d4bbc-6250-475e-843e-899cf3c11742
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
# Sort Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort</legacyLink> property to reorder the rows of a <legacyBold>Recordset</legacyBold> derived from the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database. A secondary utility routine prints each row.</para>
    <code>// BeginSortJ
import com.ms.wfc.data.*;
import java.io.* ;

public class SortX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      SortX();
      System.exit(0);
   }

   // SortX function

   static void SortX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstAuthors = null;

      // Declarations.
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" + 
                      "Initial Catalog='Pubs';Integrated Security='SSPI';";

      try
      {
         cnConn1 = new Connection();
         cnConn1.open(strCnn);
         rstAuthors = new Recordset();
         rstAuthors.setCursorLocation(AdoEnums.CursorLocation.CLIENT);
         rstAuthors.open("SELECT * FROM Authors",
               cnConn1,
               AdoEnums.CursorType.STATIC,
               AdoEnums.LockType.READONLY,
               AdoEnums.CommandType.TEXT);
         SortXprint("Initial Order",rstAuthors);

         rstAuthors.setSort("au_lname ASC, au_fname ASC");
         SortXprint("Last Name Ascending",rstAuthors);

         rstAuthors.setSort("au_lname DESC, au_fname ASC");
         SortXprint("Last Name Descending",rstAuthors);
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

   // SortXprint function

   static void SortXprint(String strTitle,Recordset rstp)
   {
      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      int intDisplaysize = 15;
      int intCount = 1;
      try
      {
         System.out.println("---------------" +
                        strTitle +
                        "---------------");
         System.out.println("First Name   Last Name" + "\n" +
                        "-------------------------" +
                        "-------------------------");
         rstp.moveFirst();
         while(!rstp.getEOF())
         {
            System.out.println(rstp.getField("au_fname").getString() +
                           "   " +
                           rstp.getField("au_lname").getString());
            if(intCount % intDisplaysize == 0)
            {
               System.out.println("\nPress &lt;Enter&gt; to continue..");
               in.readLine();
               intCount = 0;
            }
            intCount++;
            rstp.moveNext();
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
// EndSortJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>