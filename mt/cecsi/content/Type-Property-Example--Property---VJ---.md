---
title: "Type Property Example (Property) (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17438bac-468c-47ff-9028-325660e1b261
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
# Type Property Example (Property) (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property. It is a model of a utility for listing the names and types of a collection, like <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink>, <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink>, etc.</para>
    <para>We do not need to open the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to access its <legacyBold>Properties</legacyBold> collection; they come into existence when the <legacyBold>Recordset</legacyBold> object is instantiated. However, setting the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold> adds several dynamic properties to the <legacyBold>Recordset</legacyBold> object's <legacyBold>Properties</legacyBold> collection, making the example a little more interesting. For sake of illustration, we explicitly use the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property to access each <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> object.</para>
    <code>// BegintTypePropertyJ
import com.ms.wfc.data.*;
import java.io.* ;

public class TypePropertyX
{
    // The main entry point for the application.

    public static void main (String[] args)
    {
        TypePropertyX();
        System.exit(0);
    }

    // TypePropertyX  function
    static void TypePropertyX()
    {
        // Define ADO Objects.
        Recordset rst = null;
        AdoProperty prop = null;

        // Declarations.
        BufferedReader in = 
            new BufferedReader (new InputStreamReader(System.in));
        String strCnn = "DSN='Pubs';Provider='MSDASQL';Integrated Security='SSPI';";
        String strMsg;
        int intIndex;
        int intDisplaysize = 15;

        try
        {
            rst = new Recordset();
            rst.setCursorLocation(AdoEnums.CursorLocation.CLIENT);
            for(intIndex = 0; 
                intIndex &lt;= rst.getProperties().getCount() - 1;intIndex++)
            {
                prop = rst.getProperties().getItem(intIndex);
                switch(prop.getType())
                {
                    case AdoEnums.DataType.BIGINT :
                        strMsg = "adBigInt";
                        break;
                    case AdoEnums.DataType.BINARY :
                        strMsg = "adBinary";
                        break;
                    case AdoEnums.DataType.BOOLEAN :
                        strMsg = "adBoolean";
                        break;
                    case AdoEnums.DataType.BSTR :
                        strMsg = "adBSTR";
                        break;
                    case AdoEnums.DataType.CHAPTER :
                        strMsg = "adChapter";
                        break;
                    case AdoEnums.DataType.CHAR :
                        strMsg = "adChar";
                        break;
                    case AdoEnums.DataType.CURRENCY :
                        strMsg = "adCurrency";
                        break;
                    case AdoEnums.DataType.DATE :
                        strMsg = "adDate";
                        break;
                    case AdoEnums.DataType.DBDATE :
                        strMsg = "adDBDate";
                        break;
                    case AdoEnums.DataType.DBTIME :
                        strMsg = "adDBTime";
                        break;
                    case AdoEnums.DataType.DBTIMESTAMP :
                        strMsg = "adDBTimeStamp";
                        break;
                    case AdoEnums.DataType.DECIMAL :
                        strMsg = "adDecimal";
                        break;
                    case AdoEnums.DataType.DOUBLE :
                        strMsg = "adDouble";
                        break;
                    case AdoEnums.DataType.EMPTY :
                        strMsg = "adEmpty";
                        break;
                    case AdoEnums.DataType.ERROR :
                        strMsg = "adError";
                        break;
                    case AdoEnums.DataType.FILETIME :
                        strMsg = "adFileTime";
                        break;
                    case AdoEnums.DataType.GUID :
                        strMsg = "adGUID";
                        break;
                    case AdoEnums.DataType.IDISPATCH :
                        strMsg = "adIDispatch";
                        break;
                    case AdoEnums.DataType.INTEGER :
                        strMsg = "adInteger";
                        break;
                    case AdoEnums.DataType.IUNKNOWN :
                        strMsg = "adIUnknown";
                        break;
                    case AdoEnums.DataType.LONGVARBINARY :
                        strMsg = "adLongVarBinary";
                        break;
                    case AdoEnums.DataType.LONGVARCHAR :
                        strMsg = "adLongVarChar";
                        break;
                    case AdoEnums.DataType.LONGVARWCHAR :
                        strMsg = "adLongVarWChar";
                        break;
                    case AdoEnums.DataType.NUMERIC :
                        strMsg = "adNumeric";
                        break;
                    case AdoEnums.DataType.PROPVARIANT :
                        strMsg = "adPropVariant";
                        break;
                    case AdoEnums.DataType.SINGLE :
                        strMsg = "adSingle";
                        break;
                    case AdoEnums.DataType.SMALLINT :
                        strMsg = "adSmallInt";
                        break;
                    case AdoEnums.DataType.TINYINT :
                        strMsg = "adTinyInt";
                        break;
                    case AdoEnums.DataType.UNSIGNEDBIGINT :
                        strMsg = "adUnsignedBigInt";
                        break;
                    case AdoEnums.DataType.UNSIGNEDINT :
                        strMsg = "adUnsignedInt";
                        break;
                    case AdoEnums.DataType.UNSIGNEDSMALLINT :
                        strMsg = "adUnsignedSmallInt";
                        break;
                    case AdoEnums.DataType.UNSIGNEDTINYINT :
                        strMsg = "adUnsignedTinyInt";
                        break;
                    case AdoEnums.DataType.USERDEFINED :
                        strMsg = "adUserDefined";
                        break;
                    case AdoEnums.DataType.VARBINARY :
                        strMsg = "adVarBinary";
                        break;
                    case AdoEnums.DataType.VARCHAR :
                        strMsg = "adVarChar";
                        break;
                    case AdoEnums.DataType.VARIANT :
                        strMsg = "adVariant";
                        break;
                    case AdoEnums.DataType.VARNUMERIC :
                        strMsg = "adVarNumeric";
                        break;
                    case AdoEnums.DataType.VARWCHAR :
                        strMsg = "adVarWChar";
                        break;
                    case AdoEnums.DataType.WCHAR :
                        strMsg = "adWChar";
                        break;
                    default:
                        strMsg = "*UNKNOWN*";
                        break;
                }
                System.out.println("Property " +
                                   Integer.toString(intIndex) +
                                   " : " +
                                   prop.getName() +
                                   ", Type = " +
                                   strMsg);
                if(intIndex % intDisplaysize == 0 &amp;&amp; intIndex != 0)
                {
                    System.out.println("\nPress &lt;Enter&gt; to continue..");
                    in.readLine();
                }
            }

            System.out.println("\nPress &lt;Enter&gt; to continue..");
            in.readLine();
        }
        catch( AdoException ae )
        {
            // Notify user of any errors that result from ADO.

            // As passing a Recordset, check for null pointer first.
            if (rst != null)
            {
                PrintProviderError(rst.getActiveConnection());
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
         if (rst != null)
            if (rst.getState() == 1)
               rst.close();
      }
    }

    // PrintProviderError Function
    static void PrintProviderError(Connection cnn1)
    {
        // Print Provider Errors from Connection Object.
        // ErrItem is an item object in the Connections Errors Collection.
        com.ms.wfc.data.Error               ErrItem = null;
        long                                 nCount = 0;
        int                                       i = 0;

        nCount = cnn1.getErrors().getCount();

        // If there are any errors in the collection, print them.
        if ( nCount &gt; 0)
        {
            // Collection ranges from 0 to nCount-1.
            for ( i=0;i&lt;nCount; i++)
            {
                ErrItem = cnn1.getErrors().getItem(i);
                System.out.println("\t Error Number: " + ErrItem.getNumber() 
                    + "\t" + ErrItem.getDescription());
            }
        }
    }
    // PrintIOError Function
    static void PrintIOError(java.io.IOException je)
    {
        System.out.println("Error: \n");
        System.out.println("\t Source: " + je.getClass() + "\n");
        System.out.println("\t Description: "+ je.getMessage() + "\n");
    }
}
// EndTypePropertyJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
<link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>