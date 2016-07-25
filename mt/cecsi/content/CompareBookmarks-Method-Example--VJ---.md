---
title: "CompareBookmarks Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c679a15-e924-49a5-8f3a-38a8266064f8
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
# CompareBookmarks Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6">CompareBookmarks</legacyLink> method. The relative value of bookmarks is seldom needed unless a particular bookmark is somehow special.</para>
    <para>Designate a random row of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> derived from the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table as the target of a search. Then display the position of each row relative to that target.</para>
    <code>// BeginCompareBookmarksJ
import com.ms.wfc.data.*;
import java.io.* ;
import com.ms.com.*;

public class CompareBookmarksX //
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      CompareBookmarksX();
      System.exit(0);
   }

   // CompareBookmarksX function

   static void CompareBookmarksX()
   {
      // Define ADO Objects.
      Recordset rstAuthors = null;

      // Declarations.
      BufferedReader in =
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
        "Initial Catalog='Pubs';Integrated Security='SSPI';";
      int intCount;
      Variant varTarget = null;
      int intResult;
      String strAns;
      int intDisplaySize = 15;

      try
      {
         rstAuthors = new Recordset();
         rstAuthors.open("SELECT * FROM authors",
            strCnn,
            AdoEnums.CursorType.STATIC,
            AdoEnums.LockType.READONLY,
            AdoEnums.CommandType.TEXT);
         intCount = rstAuthors.getRecordCount();
         System.out.println("Rows in the Recordset = " +
            Integer.toString(intCount));

         // Exit if an empty recordset.
         if(intCount == 0)
            System.exit(0);

         // Randomize.
         intCount = (int)(intCount * Math.random());
         // Get position between 0 and count-1.
         System.out.println("\nRandomly chosen row position = " +
            Integer.toString(intCount)+ "\n");
         rstAuthors.move(intCount,new Integer(AdoEnums.Bookmark.FIRST));          // Move row to random position.
         varTarget = (Variant)rstAuthors.getBookmark();
         // Remember the mystery row.
         intCount = 0;
         rstAuthors.moveFirst();

         // Loop through recordset.
         while(!rstAuthors.getEOF())
         {
            intResult = rstAuthors.compareBookmarks
               ((Variant)rstAuthors.getBookmark(), varTarget);
            if(intResult == AdoEnums.Compare.NOTEQUAL)
               System.out.println("Row " +
                  Integer.toString(intCount) +
                  ": Bookmarks are not equal.");
            else if(intResult == AdoEnums.Compare.NOTCOMPARABLE)
               System.out.println("Row " +
                  Integer.toString(intCount) +
                  ": Bookmarks are not comparable.");
            else
            {
               switch(intResult)
               {
               case AdoEnums.Compare.LESSTHAN :
                  strAns = "less than";
                  break;
               case AdoEnums.Compare.EQUAL :
                  strAns = "equal to";
                  break;
               case AdoEnums.Compare.GREATERTHAN :
                  strAns = "greater than";
                  break;
               default :
                  strAns = "in error comparing to";
                  break;
               }
               System.out.println("Row position " +
                  Integer.toString(intCount) +
                  " is " + strAns + " the target.");
            }
            if(intCount % intDisplaySize == 0 &amp;&amp; intCount &gt; 0)
            {
               System.out.println("\nPress &lt;Enter&gt; to continue..");
               in.readLine();
            }
            intCount++;
            rstAuthors.moveNext();
         }

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

// EndCompareBookmarksJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6">CompareBookmarks Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>