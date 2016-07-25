---
title: "Item Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1426a08-71b8-4af2-9f57-97ceb90ccef2
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
# Item Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property accesses members of a collection. The example opens the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database with a parameterized command.</para>
    <para>The parameter in the command issued against the database is accessed from the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object's <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection by index and name. Then the fields of the returned <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> are accessed from that object's <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection by index and name.</para>
    <code>// BeginItemJ
import com.ms.wfc.data.*;
import java.io.* ;
import com.ms.com.*;

public class ItemX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      ItemX();
      System.exit(0);
   }

   // ItemX  function

   static void ItemX()
   {

      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstAuthors = null;
      Command cmd = null;
      Parameter prm = null;
      Field fld = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
            "Initial Catalog='Pubs';Integrated Security='SSPI';";
      Variant [] varColumn = null;
      int intIndex;
      int intLimit;

      try
      {
         cnConn1 = new Connection();
         rstAuthors = new Recordset();
         cmd = new Command();

         //  Set the array with the Authors table field (column) names.
         varColumn = new Variant[9];
         varColumn[0] = new Variant("au_id");
         varColumn[1] = new Variant("au_lname");
         varColumn[2] = new Variant("au_fname");
         varColumn[3] = new Variant("phone");
         varColumn[4] = new Variant("address");
         varColumn[5] = new Variant("city");
         varColumn[6] = new Variant("state");
         varColumn[7] = new Variant("zip");
         varColumn[8] = new Variant("contract");

         cmd.setCommandText("SELECT * FROM Authors WHERE state = ?");
         prm = cmd.createParameter("ItemXparm",
                             AdoEnums.DataType.CHAR,
                             AdoEnums.ParameterDirection.INPUT,
                             2,
                             "CA");
         cmd.getParameters().append(prm);

         cnConn1.open(strCnn);
         cmd.setActiveConnection(cnConn1);

         // Connection and CommandType are omitted
         // because a Command Object is provided.
         rstAuthors.open(cmd,
                null ,
                AdoEnums.CursorType.STATIC,
                AdoEnums.LockType.READONLY);

         System.out.println(
            "The Parameters collection accessed by index...");
         prm = cmd.getParameters().getItem(0);
         System.out.println("Parameter name = '" +
                        prm.getName() +
                        "', value = '" +
                        prm.getValue().toString() + "'\n");

         System.out.println(
            "The Parameters collection accessed by name...");
         prm = cmd.getParameters().getItem("ItemXparm");
         System.out.println("Parameters name = '" +
                        prm.getName() +
                        "', value = '" +
                        prm.getValue().toString() + "'\n");
         System.out.println("Press &lt;Enter&gt; to continue..");
         in.readLine();

         System.out.println(
            "The Fields collection accessed by index...");
         rstAuthors.moveFirst();
         intLimit = rstAuthors.getFields().getCount() - 1;
         for(intIndex = 0; intIndex &lt;= intLimit; intIndex++)
         {
            fld = rstAuthors.getFields().getItem(intIndex);
            short intVtType = fld.getValue().getvt();
            String strFieldValue;
            switch(intVtType)
            {
            case Variant.VariantString :
               strFieldValue = fld.getValue().toString();
               break;
            case Variant.VariantBoolean :
               if(fld.getValue().getBoolean())
                  strFieldValue = "True";
               else
                  strFieldValue = "False";
               break;
            default :
               strFieldValue = fld.getValue().toString();
               break;
            }
            System.out.println("Field " +
                           Integer.toString(intIndex) +
                           " : Name = '" +
                           fld.getName() +
                           "', value = '" +
                           strFieldValue +
                           "'");
         }
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();

         System.out.println("The Fields collection accessed by name...");
         rstAuthors.moveFirst();
         for(intIndex = 0; intIndex &lt;= 8; intIndex++)
         {
            fld = rstAuthors.getFields().getItem
               (varColumn[intIndex].toString());
            short intVtType = fld.getValue().getvt();
            String strFieldValue;
            switch(intVtType)
            {
            case Variant.VariantString :
               strFieldValue = fld.getValue().toString();
               break;
            case Variant.VariantBoolean :
               if(fld.getValue().getBoolean())
                  strFieldValue = "True";
               else
                  strFieldValue = "False";
               break;
            default :
               strFieldValue = fld.getValue().toString();
               break;
            }
            System.out.println("Field " +
                           "name = '" +
                           fld.getName() +
                           "', value = '" +
                           strFieldValue +
                           "'");
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
// EndItemJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item Property</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>