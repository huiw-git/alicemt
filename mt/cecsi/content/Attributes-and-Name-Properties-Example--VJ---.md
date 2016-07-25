---
title: "Attributes and Name Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 625f8bcb-a9bb-4534-8768-00a9bcbe7b7f
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
# Attributes and Name Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example displays the value of the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property for <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>, and <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> objects. It uses the <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property to display the name of each <legacyBold>Field</legacyBold> and <legacyBold>Property</legacyBold> object.</para>
    <code>// BeginAttributesJ
import com.ms.wfc.data.*;
import java.io.*;

public class AttributesX
{
   // The main entry point for the application
   public static void main (String[] args)
   {
      AttributesX();
      System.exit(0);
   }

   // AttributeX Function

   static void AttributesX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstEmployees = null;
      Fields listOfFields = null;
      AdoProperties listOfProperties = null;

      //Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";
      int recordDisplaySize = 15;
      int propertyCount = 0;
      try
      {
         // Open connection and recordset.
         cnConn1 = new Connection();
         cnConn1.open(strCnn);

         rstEmployees = new Recordset ();
         rstEmployees.open("employee", 
            cnConn1,AdoEnums.CursorType.FORWARDONLY, 
            AdoEnums.LockType.READONLY, AdoEnums.CommandType.TABLE);

         // Display the attributes of the connection.
         System.out.println("Connection attributes = " 
            + cnConn1.getAttributes());
         // Display the attributes of the Employees table's fields.
         System.out.println("\n\nField attributes : " + "\n");

         listOfFields = rstEmployees.getFields();

         for ( int i=0; i &lt; listOfFields.getCount();i++)
         {
            System.out.println("\t\t" + listOfFields.getItem(i).getName()
               + " = " + listOfFields.getItem(i).getAttributes());
         }

         // Display fields of the Employees table which are NULLABLE.
         System.out.println("\n\nNULLABLE Fields : " + "\n");
         for ( int i=0; i &lt; listOfFields.getCount();i++)
         {
            if ((listOfFields.getItem(i).getAttributes() &amp; 
               AdoEnums.FieldAttribute.ISNULLABLE) &gt; 0)
               System.out.println("\t\t" + 
               listOfFields.getItem(i).getName());

         }

         System.out.println ("\n\nPress &lt;Enter&gt; key to continue..");
         line = in.readLine();

         // Display the attributes of the Employees table's properties.
         System.out.println("\n\nProperty attributes : " );
         listOfProperties = rstEmployees.getProperties();
         for ( int i=0; i &lt; listOfProperties.getCount() ;i++)
         {
            System.out.println("\t\t" + 
               listOfProperties.getItem(i).getName()
               + " = " + listOfProperties.getItem(i).getAttributes());

            if (propertyCount == recordDisplaySize)
            {
               System.out.println ("\n\nPress &lt;Enter&gt; key to continue.");
               line = in.readLine();
               propertyCount = 0;
            }
            propertyCount++;
         }

         System.out.println ("\n\nPress &lt;Enter&gt; key to continue.");
         line = in.readLine();
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if (rstEmployees.getActiveConnection()==null)
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

   //.PrintIOError Function
   
   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}

// EndAttributesJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name Property</link>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>