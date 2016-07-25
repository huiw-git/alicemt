---
title: "ConnectionString, ConnectionTimeout, and State Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c1e61ed-6569-44a9-b0c8-75b820a64cb6
caps.latest.revision: 11
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
# ConnectionString, ConnectionTimeout, and State Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates different ways of using the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to open a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout</legacyLink> property to set a connection time-out period, and the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property to check the state of the connections. The GetState function is required for this procedure to run.</para>
    <alert class="note">
      <para>   If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
    </alert>
    <code>// BeginConnectionStringJ
import com.ms.wfc.data.*;
import java.io.* ;

public class ConnectionStringX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      ConnectionStringX();
      System.exit(0);
   }

   // ConnectionStringX function

   static void ConnectionStringX()
   {
      // Define ADO Objects.
      Connection cnConn1 = null;
      Connection cnConn2 = null;
      Connection cnConn3 = null;
      Connection cnConn4 = null;

      //Declarations.

      BufferedReader in =
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strTemp;

      try
      {
         // Open a connection using OLE DB syntax.
         cnConn1 = new Connection();
         cnConn1.setConnectionString(
            "Provider='sqloledb';Data Source='MySqlServer';" +
            "Initial Catalog='Pubs';Integrated Security='SSPI';");
         cnConn1.setCommandTimeout(30);
         cnConn1.open();
         strTemp = getState(cnConn1.getState());
         System.out.println("CnConn1 state: " + strTemp);

         // Open a connection using a DSN and ODBC tags.
         // It is assumed that you have create DSN 'Pubs' with a user name as 
         // 'MyUserId' and password as 'MyPassword'.
         cnConn2 = new Connection();
         cnConn2.setConnectionString("DSN='Pubs';UID='MyUserId';PWD='MyPassword';");
         cnConn2.open();
         strTemp = getState(cnConn2.getState());
         System.out.println("CnConn2 state: " + strTemp);

         // Open a connection using a DSN and OLE DB tags.
         cnConn3 = new Connection();
         cnConn3.setConnectionString
            ("Data Source='Pubs';");
         cnConn3.open();
         strTemp = getState(cnConn3.getState());
         System.out.println("CnConn3 state: " + strTemp);

         // Open a connection using a DSN and individual
         // arguments instead of a connection string.
         // It is assumed that you have create DSN 'Pubs' with a user name as 
         // 'MyUserId' and password as 'MyPassword'.
         cnConn4 = new Connection();
         cnConn4.open("Pubs", "MyUserId", "MyPassword");
         strTemp = getState(cnConn4.getState());
         System.out.println("CnConn4 state: " + strTemp);
         
         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         System.out.println("Exception: " + ae.getMessage());

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
         if (cnConn2 != null)
            if (cnConn2.getState() == 1)
               cnConn2.close();  
         if (cnConn3 != null)
            if (cnConn3.getState() == 1)
               cnConn3.close();  
         if (cnConn4 != null)
            if (cnConn4.getState() == 1)
               cnConn4.close();
      }

   }

   // getState Function

   static String getState(int intState)
   {
      // Returns current state of the connection object.
      String strState=null;

      switch(intState)
      {
      case AdoEnums.ObjectState.CLOSED :
         strState = new String("adStateClosed");
         break;
      case AdoEnums.ObjectState.OPEN  :
         strState = new String("adStateOpen");
         break;
      default :
         break;
      }
      return strState;
   }

   // PrintIOError Function

   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}

// EndConnectionStringJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
<link xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout Property</link>
<link xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>