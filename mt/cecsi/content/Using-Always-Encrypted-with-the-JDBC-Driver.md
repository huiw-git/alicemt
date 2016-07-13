---
title: Using Always Encrypted with the JDBC Driver
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
manager: jhubbard
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
# Using Always Encrypted with the JDBC Driver
  Always Encrypted allows clients to encrypt sensitive data inside client applications and never reveal the encryption keys to SQL Server. An Always Encrypted enabled driver installed on the client computer achieves this by automatically encrypting and decrypting sensitive data in the SQL Server client application. The driver encrypts the data in sensitive columns before passing the data to SQL Server, and automatically rewrites queries so that the semantics to the application are preserved. Similarly, the driver transparently decrypts data stored in encrypted database columns that are contained in query results. For more information, see [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/library/mt163865.aspx), and [Always Encrypted API Reference for the JDBC Driver](../content/Always-Encrypted-API-Reference-for-the-JDBC-Driver.md)  
  
> [!NOTE]  
>  Always Encrypted is supported only by Microsoft JDBC Driver 6.0 or higher for SQL Server with SQL Server 2016 or higher. 
  
  
## Developing client applications for accessing Always Encrypted data  
Querying a database using Always Encrypted from a client application requires minimal development effort. The following summarizes the prerequisites and steps you must take for your application to read and write Always Encrypted data.  
  
### Prerequisites  
  
-   Configure the server by following the directions in the **Getting Started with Always Encrypted** section of the [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/library/mt163865.aspx) topic.  
  
-   Install **Microsoft JDBC Driver 6.0 for SQL Server** on the client computer.  
  
-   Download and install the Java Cryptography Extension \(JCE\) Unlimited Strength Jurisdiction Policy Files.  Be sure to read the Readme included in the zip file for installation instructions and pertinent details on possible export\/import issues.  
  
    -   If using the sqljdbc41.jar, the policy files can be downloaded from [Java Cryptography Extension \(JCE\) Unlimited Strength Jurisdiction Policy Files 7 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)  
  
    -   If using the sqljdbc42.jar, the policy files can be downloaded from  [Java Cryptography Extension \(JCE\) Unlimited Strength Jurisdiction Policy Files 8 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)  
  
### Set up the client application  
 The client application must be configured to have access to a key store containing a Column Master Key \(CMK\) protecting the data the application is going to access. For information about column master keys, see [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/library/mt163865.aspx). The JDBC driver comes with implementations for three system store providers:

- **SQLServerColumnEncryptionAzureKeyVaultProvider** which can be used to store column master keys in the Azure Key Vault.
- **SQLServerColumnEncryptionCertificateStoreProvider** which can be used to store column master keys in Windows Certificate Store.
- **SQLServerColumnEncryptionJavaKeyStoreProvider** which can be used to store column master keys in the Java keystore in JKS or PKCS12 format.

You can use a custom key store provider by extending the SQLServerColumnEncryptionKeyStoreProvider class and registering it using the SQLServerConnection.registerColumnEncryptionKeyStoreProviders() method.     

All of these key store providers are described in more detail below.
  
### Using Azure Key Vault for column master key
The JDBC Driver users can use keys stored in Azure Key Vault \(AKV\) with a key store provider called SQLServerColumnEncryptionAzureKeyVaultProvider. The name of the Azure Key Vault store provider is AZURE\_KEY\_VAULT. In order to use the Azure Key Vault store provider, user needs to create the vault and the keys in Azure and configure the application to access the keys. Refer to [Azure Key Vault – Step by Step for more information on setting up the key vault](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/).  
  
To use the Azure Key Vault, client applications need to instantiate the SQLServerColumnEncryptionAzureKeyVaultProvider and register it with the driver. The JDBC driver delegates authentication to user though an interface called SQLServerKeyVaultAuthenticationCallback which has a method for retrieving an access token for the user’s vault. To instantiate the Azure Key Vault store provider, user needs to provide an implementation for the only method called **getAccessToken** that retrieves the access token for user’s key stored in Azure Key Vault.  
  
Here is an example of initializing SQLServerKeyVaultAuthenticationCallback and SQLServerColumnEncryptionAzureKeyVaultProvider:  
  
```  
// String variables clientID and clientSecret hold the client id and client secret values respectively.  
  
ExecutorService service = Executors.newFixedThreadPool(10);  
SQLServerKeyVaultAuthenticationCallback authenticationCallback = new SQLServerKeyVaultAuthenticationCallback() {  
       @Override  
	public String getAccessToken(String authority, String resource, String scope) {  
		AuthenticationResult result = null;  
		try{  
		        AuthenticationContext context = new AuthenticationContext(authority, false, service);  
			ClientCredential cred = new ClientCredential(clientID, clientSecret);  
  
			Future<AuthenticationResult> future = context.acquireToken(resource, cred, null);  
			result = future.get();  
		}  
		catch(Exception e){  
			e.printStackTrace();  
		}  
		return result.getAccessToken();  
	}  
};  
  
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(authenticationCallback, service);  
  
```  
  
When creating a CMK, use AZURE\_KEY\_VAULT as the KEY\_STORE\_PROVIDER\_NAME. This name can be retrieved by the API SQLServerColumnEncryptionAzureKeyVaultProvider.getName() and use Key ID as the KEY\_PATH. You can also use SQL Server Management Studio to create CMK definitions for Azure Key Vault. 

To register the Azure Key Vault store provider use the SQLServerConnection.registerColumnEncryptionKeyStoreProviders\(\) method. You can register multiple key vault providers with the JDBC driver and the driver will automatically detect which provider to use based on the encryption metadata of the column. For more details on the API for registering key store providers, see [Always Encrypted API Reference for the JDBC Driver](../content/Always-Encrypted-API-Reference-for-the-JDBC-Driver.md).  
  
You can use SQL Server Management Studio to create column encryption key definition for a column master key stored in the Azure Key Vault. Alternatively you can encrypt the plain text key using the JDBC driver and create the CEK definition in the database using T-SQL commands. The SQLServerColumnEncryptionAzureKeyVaultProvider.encryptColumnEncryptionKey\(\) method can be used to encrypt a plaintext CEK provided by the user. This method takes the Key ID as the CMK path, the algorithm \(the only accepted algorithm is ‘RSA\_OAEP’\), and the plain text CEK value, and returns the encrypted CEK. You can then use [CREATE COLUMN ENCRYPTION KEY](https://msdn.microsoft.com/library/mt146372.aspx) T-SQL command to create the CEK.     


> [!IMPORTANT]  
>  The Azure Key Vault implementation of the JDBC driver has  dependencies  on these libraries \(from GitHub\):  
>   
>  [azure\-sdk\-for\-java](https://github.com/Azure/azure-sdk-for-java)  
>   
>  [azure\-activedirectory\-library\-for\-java libraries](https://github.com/AzureAD/azure-activedirectory-library-for-java)  
  
### Using Windows Certificate Store for column master key
The SQLServerColumnEncryptionCertificateStoreProvider can be used to store column master keys in the Windows Certificate Store. Use the SQL Server Management Studio (SSMS) Always Encrypted wizard to create the column master key and column encryption key definitions in the database. The same wizard can be used to generate a self signed certificate in the Windows Certificate Store that be used as a column master key for the always encrypted data. For more information on column master key and column encryption key T-SQL syntax visit [CREATE COLUMN MASTER KEY](https://msdn.microsoft.com/library/mt146393.aspx) and [CREATE COLUMN ENCRPTION KEY](https://msdn.microsoft.com/library/mt146372.aspx) respectively.

The name of the SQLServerColumnEncryptionCertificateStoreProvider is "MSSQL_CERTIFICATE_STORE" and can be queried by the getName() API of the provider object. It is automatically registered by the driver and can be used seamlessly without any application change.

> [!IMPORTANT]  
>  The SQLServerColumnEncryptionCertificateStoreProvider implementation of the JDBC driver is available with Windows operating systems only and has a dependency on the SQLJDBC_AUTH.DLL that is available in the driver package.  
  
### Using Java Key Store for column master key  
The JDBC driver comes with a built in key store provider implementation for the Java Key Store. Client applications need to pass the required credentials for the key store in the connection string or through the SQLServerDataSource object. The name of the Java key store provider is MSSQL\_Java\_KEYSTORE. This name can also be queried by the SQLServerColumnEncryptionJavaKeyStoreProvider.getName() API. The following three connection  properties need to be set to use the Java Key Store.
  
 **keyStoreAuthentication:** Identifies the Key Store to use. For the Java Key Store the value for this setting must be "JavaKeyStorePassword".  
  
 **keyStoreLocation:** The path to the Java keystore file that stores the column master key. Note that the path includes the keystore filename.  
  
 **keyStoreSecret:** The secret/password to use for the keystore as well as for the key. Note that for using the Java Key Store the keystore and the key password must be the same.  

Here is an example on providing these credentials in connection string:

    String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_passowrd>";
    
These settings can also be set/get using the SQLServerDataSource object. See [Always Encrypted API Reference for the JDBC Driver](../content/Always-Encrypted-API-Reference-for-the-JDBC-Driver.md) for more information.     
  
The JDBC driver automatically instantiates the SQLServerColumnEncryptionJavaKeyStoreProvider when these credentials are present in connection properties. 
  
### Creating a Column Master Key \(CMK\) for the Java Key Store
The SQLServerColumnEncryptionJavaKeyStoreProvider can be used with JKS or PKCS12 keystore types. To create or import a key to use with this provider use the Java [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) utility. Please note that the key must have the same password as the keystore itself. Here is an example of how to create a public key and it's associated private key using the keytool utility.

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks    

This command creates a public key and wraps it in a X.509 self signed certificate which is then stored in the keystore 'keystore.jks' along with it's associated private key. This entry in the keystore is identified by the alias 'AlwaysEncryptedKey'. 

Here is an example of the same using a PKCS12 storetype. 

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword   

Note that if the keystore is of type PKCS12 then the keytool utility does not prompt for key password and the key password needs to be provided with -keypass option as the SQLServerColumnEncryptionJavaKeyStoreProvider requires that the keystore and the key have the same password.

You can also export a certificate from the Windows Certificate store in .pfx format and use that with the SQLServerColumnEncryptionJavaKeyStoreProvider. The exported certificate can also be imported to the Java key store as a JKS keystore type. 

After creating the keytool entry you will have to create the column master key meta data in the database which needs the key store provider name and the key path. For more information on how to create CMK meta data visit [CREATE COLUMN MASTER KEY](https://msdn.microsoft.com/library/mt146393.aspx). For SQLServerColumnEncryptionJavaKeyStoreProvider, the key path is just the alias of the key. And the name of the SQLServerColumnEncryptionJavaKeyStoreProvider is 'MSSQL_JAVA_KEYSTORE'. You can also query this name using the getName() public API of the SQLServerColumnEncryptionJavaKeyStoreProvider class. 

The T-SQL syntax for creating the column master key is:

```  
CREATE COLUMN MASTER KEY [<CMK_name>]  
WITH  
(  
	KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',  
	KEY_PATH = N'<key_alias>'  
)  
```  

For the 'AlwaysEncryptedKey' created above, the column master key definition would be:

```  
CREATE COLUMN MASTER KEY [MYCMK]
WITH
(
	KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
	KEY_PATH = N'AlwaysEncryptedKey'
)
```  
    
> [!NOTE]  
>  The built in SQL Server management Studio functionality cannot create CMK definitions for the Java Key Store for which you must use T-SQL command.  
  
### Creating a Column Encryption Key \(CEK\) for the Java Key Store  
The SQLServerColumnEncryptionJavaKeyStoreProvider.encryptColumnEncryptionKey\(\) method can be used to encrypt a plain text column encryption key provided by the user. This method takes the CMK path \(note: the CMK needs to be in the Java Key Store\), the algorithm \(the only accepted algorithm is ‘RSA\_OAEP’\), and the plain text CEK value, and returns the encrypted CEK. A CEK definition can then be created in the database by the T\-SQL command as described in [CREATE COLUMN ENCRPTION KEY](https://msdn.microsoft.com/library/mt146372.aspx). A sample code for creating a CEK is provided below. It is also included in the samples directory of the download package.  
  
```  
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create Column Master Key (CMK) and Column Encryption Key (CEK)
 * CMK is created first and then it is used to create CEK
 */
public class AlwaysEncrypted
{
	// Alias of the key stored in the keystore.
	private static String keyAlias = "<proide key alias>";

	// Name by which the column master key will be known in the database.
	private static String columnMasterKeyName = "JDBC_CMK";

	// Name by which the column encryption key will be known in the database.
	private static String columnEncryptionKey = "JDBC_CEK";

	// The location of the keystore. 
	private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

	// The password of the keystore and the key.
	private static char[] keyStoreSecret = "********".toCharArray();

	/**
	 * Name of the encryption algorithm used to encrypt the value of
	 * the column encryption key. The algorithm for the system providers must be RSA_OAEP.
	 */
	private static String algorithm = "RSA_OAEP";

	public static void main(String[] args)
	{
		String connectionString = GetConnectionString();
		try
		{
			// Note: if you are not using try-with-resources statements (as here),
			// you must remember to call close() on any Connection, Statement,
			// ResultSet objects that you create.

			// Open a connection to the database.
			Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
			try (Connection sourceConnection = DriverManager.getConnection(connectionString))
			{
				// Instantiate the Java Key Store provider.
				SQLServerColumnEncryptionKeyStoreProvider storeProvider = 
						new SQLServerColumnEncryptionJavaKeyStoreProvider(
								keyStoreLocation,
								keyStoreSecret);

				/**
				 * Create column mater key
				 * For details on syntax  refer: 
				 * https://msdn.microsoft.com/library/mt146393.aspx
				 * 
				 */
				String createCMKSQL = "CREATE COLUMN MASTER KEY " 
						+ columnMasterKeyName
						+ " WITH ( "
						+ " KEY_STORE_PROVIDER_NAME = '" 
						+ storeProvider.getName()
						+ "' , KEY_PATH =  '" 
						+ keyAlias
						+ "' ) ";

				try (Statement cmkStatement = sourceConnection.createStatement())
				{
					cmkStatement.executeUpdate(createCMKSQL);
					System.out.println("Column Master Key created with name : " + columnMasterKeyName);
				}
				
				byte [] encryptedCEK=getEncryptedCEK(storeProvider);

				/**
				 * Create column encryption key 
				 * For more details on the syntax refer: 
				 * https://msdn.microsoft.com/library/mt146372.aspx
				 * Encrypted CEK first needs to be converted into varbinary_literal from bytes, 
				 * for which DatatypeConverter.printHexBinary is used
				 */
				String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY " 
						+ columnEncryptionKey
						+ " WITH VALUES ( "
						+ " COLUMN_MASTER_KEY = " 
						+ columnMasterKeyName
						+ " , ALGORITHM =  '" 
						+ algorithm
						+ "' , ENCRYPTED_VALUE =  0x" 
						+ DatatypeConverter.printHexBinary(encryptedCEK)
						+ " ) ";

				try (Statement cekStatement = sourceConnection.createStatement())
				{
					cekStatement.executeUpdate(createCEKSQL);
					System.out.println("CEK created with name : " + columnEncryptionKey);
				}
			}
		}
		catch (Exception e)
		{
			// Handle any errors that may have occurred.
			e.printStackTrace();
		}
	}

	// To avoid storing the sourceConnection String in your code,
	// you can retrieve it from a configuration file.
	private static String GetConnectionString()
	{

		// Create a variable for the connection string.
		String connectionUrl = "jdbc:sqlserver://localhost:1433;" +
				"databaseName=ae2;user=sa;password=********;";

		return connectionUrl;
	}

	private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException
	{
		/**
		 * Following arguments needed by  SQLServerColumnEncryptionJavaKeyStoreProvider
		 * 1) keyStoreLocation : 
		 * 		Path where keystore is located, including the keystore file name. 
		 * 2) keyStoreSecret : 
		 * 		Password of the keystore and the key.  
		 */
		String plainTextKey = "You need to give your plain text";

		// plainTextKey has to be 32 bytes with current algorithm supported
		byte[] plainCEK = plainTextKey.getBytes();

		// This will give us encrypted column encryption key in bytes
		byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(
				keyAlias,
				algorithm,
				plainCEK);

		return encryptedCEK;
	}
}

```  
  
> [!NOTE]  
>  The built in SQL Server management Studio functionality can not be used to create CEKs using CMKs in the Java Key Store, use the method illustrated in sample code above to create a CEK instead.  
    
### Enabling Always Encrypted for a client connection  
 Modify the connection string in your client application by adding the columnEncryptionSetting\=Enabled parameter to the connection string.  
  
 The following is an example of a connection string for the Microsoft JDBC Driver 6.0 that enables Always Encrypted:  
  
```  
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";  
```  
  
 Always Encrypted can also be enabled by the using the SQLServerDataSource object as follows:  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setColumnEncryptionSetting("Enabled");  
```    

Note that to use the Java Key Store provider you need to provide additional credentials in the connection string. See **Using Java Key Store provider for storing column master key** section for more details.
  
### Enabling Always Encrypted on a statement  
 If you do not need to turn on Always Encrypted for the whole connection, you can also turn on this setting on a per statement basis. When creating a statement, you can pass in an Enum, **SQLServerStatementColumnEncryptionSetting**, which specifies how data will be sent and received when reading and writing encrypted columns for that specific statement. Depending on your specific query, performance impact may be reduced by bypassing the Always Encrypted driver’s processing when non\-encrypted columns are being used. Note that these settings cannot be used to bypass encryption and gain access to plaintext data. For more details on how to configure column encryption on a statement, see [Always Encrypted API Reference for the JDBC Driver](../content/Always-Encrypted-API-Reference-for-the-JDBC-Driver.md).  
  
### Inserting\/Retrieving data example  
 Insert data into encrypted columns by using SQLServerPreparedStatement or SQLServerCallableStatement objects. The application passes plaintext values in the PreparedStatement or CallableStatement set methods. The driver then transparently encrypts these values and passes the encrypted values to the server. Similarly when encrypted columns are retrieved via ResultSet objects, the driver transparently decrypts the values before sending the values to the application. When a column is encrypted no plaintext data is available to the SQL Server; it only sends\/receives encrypted data.  
  
 Example of how to insert\/retrieve values to\/from encrypted columns:  
  
```  
import java.sql.*;  
    
public class AlwaysEncrypted  
{  
  
    // Name of the table.   
    private static String tblName = "Customers";  
  
    // Name of the column encryption key to be used for encryption.   
    private static String columnEncryptionKey = "JDBC_CEK";  
 
	// The location of the keystore. 
	private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,  
            // ResultSet objects that you create.  
  
            // Open a sourceConnection to the database.  
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                /**  
                 * Query to create table with Always Encrypted feature  
                 * For details on the syntax please refer : https://msdn.microsoft.com/library/ms174979.aspx  
                 */  
                String createTblSQL = "CREATE TABLE " + tblName  
                    + " ( "  
                    + " FIRST_NAME varchar(100) "
                    	+ "COLLATE Latin1_General_BIN2 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,"
                    	+ "ALGORITHM='AEAD_AES_256_CBC_HMAC_SHA_256',COLUMN_ENCRYPTION_KEY="+columnEncryptionKey+"),"  
                    + " LAST_NAME varchar(100) "
                    	+ "COLLATE Latin1_General_BIN2 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,"
                    	+ "ALGORITHM='AEAD_AES_256_CBC_HMAC_SHA_256',COLUMN_ENCRYPTION_KEY="+columnEncryptionKey+"),"  
                    + " SSN int "
                    	+ "ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,"
                    	+ "ALGORITHM='AEAD_AES_256_CBC_HMAC_SHA_256',COLUMN_ENCRYPTION_KEY="+columnEncryptionKey+")"  
                    + " ) ";  
  
                try (Statement createTblStatement = sourceConnection.createStatement())  
                {  
                    // Create the table.   
                    createTblStatement.executeUpdate(createTblSQL);  
                    System.out.println("Table created with name : " + tblName + "\n");  
                }  
  
                // Insert records in the table.   
                String insertRecord="INSERT INTO " + tblName + " values (?,?,?)";  
  
                try (PreparedStatement insertStatement = sourceConnection.prepareStatement(insertRecord))  
                {  
                    insertStatement.setString(1, "First Name");   
                    insertStatement.setString(2, "Last Name");  
                    insertStatement.setInt(3, 1);  
                    insertStatement.executeUpdate();  
                    System.out.println("Record inserted.\n");  
                }  
  
                // Retrieve records from the table.  
                // Note: To filter data based on encrypted column values, use PreparedStatement parameters.   
                String selectRecord="Select * from " + tblName;  
                try (PreparedStatement selectStatement = sourceConnection.prepareStatement(selectRecord))  
                {  
                    ResultSet rs = selectStatement.executeQuery();  
                    System.out.println("Getting records from the database...");  
                    while(rs.next()) {  
                        System.out.println("First name of customer : " + rs.getString("FIRST_NAME"));  
                        System.out.println("Last name of customer : " + rs.getString("LAST_NAME"));  
                        System.out.println("SSN of customer : " + rs.getInt("SSN"));  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,  
    // you can retrieve it from a configuration file.  
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
            "databaseName=ae;user=sa;password=*******;columnEncryptionSetting=Enabled;" +
            "keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=" + keyStoreLocation + 
            ";keyStoreSecret=********;";  
        return connectionUrl;  
    }  
}  
```  
  
> [!NOTE]  
>  Queries can perform equality comparisons on columns if they are encrypted using deterministic encryption. For more information, see the **Selecting Deterministic or Randomized encryption** section of the [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/library/mt163865.aspx) topic.  
  
### Registering a custom column master key store provider  
 Information the driver receives from SQL Server for query parameters which need to be encrypted, and for query results which need to be decrypted, includes:  
  
-   An encrypted value of a column encryption key, which should be used to encrypt or decrypt a parameter or a result.  
  
-   The name of a key store provider that encapsulates a key store containing the column master key which was used to encrypt the column encryption key.  
  
-   A key path that specifies the location of the column master key in the key store.  
  
-   The name of the algorithm that was used to encrypt the column encryption key.  
  
 The driver uses the above information to use the key store provider implementation to decrypt the retrieved encrypted value of the column encryption key, which is subsequently used to either encrypt a query parameter or to decrypt a query result.  
  
The driver comes with an implementation of three key store providers, SQLServerColumnEncryptionJavaKeyStoreProvider, SQLServerColumnEncryptionAzureKeyVaultProvider and SQLServerColumnEncryptionCertificateStoreProvider.  
  
 You can also use a custom key store provider by extending the SQLServerColumnEncryptionKeyStoreProvider class and registering it using the SQLServerConnection.registerColumnEncryptionKeyStoreProviders\(\) method.  
For details, see the example below:  
:  
  
```  
public class MyCustomKeyStore extends SQLServerColumnEncryptionKeyStoreProvider{  
	private String name = "MY_CUSTOM_KEYSTORE";
	
	public void setName(String name)
	{
		this.name = name;
	}
	
	public String getName()
	{
		return name;
	}

    public byte[] encryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)  
	{  
		// Code for encrypting the CEK  
	}  
	
    public byte[] decryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)  
	{  
		// Code for decrypting the CEK  
	}  
}  
  
```  
  
 Register the provider:  
  
```  
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();  
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();  
keyStoreMap.put(storeProvider.getName(), storeProvider);  
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);  
  
```  
  
 Any column master key stored in a key store must be defined in the database using [CREATE COLUMN MASTER KEY \(Transact\-SQL\)](https://msdn.microsoft.com/library/mt146393.aspx). The key store provider name in the definition of the column master key must match the provider name registered in the client application.  A CMK definition for this custom provider would look like:  
  
```  
CREATE COLUMN MASTER KEY [MyCustomCMK]  
WITH  
(  
	KEY_STORE_PROVIDER_NAME = N'MY_CUSTOM_KEYSTORE',  
	KEY_PATH = N'<My_Custom_Path>'  
)  
  
```  
  
 The CEK needs to be encrypted by calling MyCustomKeyStore.encryptColumnEncryptionKey\(\) method, and then needs to be created in the database using the CREATE COLUMN ENCRYPTION KEY T\-SQL command. Any columns encrypted with this CEK can now use the custom key store provider with Always Encrypted data.  
  
### Force encryption on input parameters  
 The Force Encryption feature enforces encryption of a parameter when using Always Encrypted. If force encryption is used and SQL Server informs the driver that the parameter does not need to be encrypted, the query using the parameter will fail. This property provides additional protection against security attacks that involve a compromised SQL Server providing incorrect encryption metadata to the client, which may lead to data disclosure. The set\* methods in SQLServerPreparedStatement and SQLServerCallableStatement classes and the update\* methods in the SQLServerResultSet class are overloaded to accept a boolean argument to specify force encryption setting. If the value of this argument is false, the driver will not force encryption on parameters. If force encryption is set to true, the query parameter will only be set if the destination column is encrypted and Always Encrypted is enabled on the connection or on the statement. This gives an extra layer of security, ensuring that no data is mistakenly written to an unencrypted column when it is expected to be encrypted.  
  
 For more information on the SQLServerPreparedStatement and SQLServerCallableStatement methods that are overloaded with the force encryption setting, see [Always Encrypted API Reference for the JDBC Driver](../content/Always-Encrypted-API-Reference-for-the-JDBC-Driver.md)  
  
### Configuring CEK cache time-to-live value
The JDBC driver caches the plain text value of the column encrytion key for optimizing performance. When a CEK is used for the first time, the driver decrypts it's encrypted value using the CMK and caches the decrypted value. If the same CEK is used in subsequent queries then the driver can just get the plain text key from the cache thus optimizing performance. The time-to-live value for the CEKs in the cache is configurable by the setColumnEncryptionKeyCacheTtl() API in the SQLServerConnection class. The default time-to-live value for the cache is 2 hours. To turn off caching use a value of 0. To set any time-to-live value use the following API:
    
    setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
   
For example, to set a time-to-live value of 10 minutes, use
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)  

### Configuring how java.sql.Time values are sent to the server
The sendTimeAsDatetime connection property is used to configure how the java.sql.Time value is sent to the server. When sendTimeAsDatetime=false, the time value is sent as SQL Server time type and when sendTimeAsDatetime=true, the time value is sent as a datetime type. Not that, when a time column is encrypted, the sendTimeAsDatetime property must be false as encrypted columns do not support the conversion from time to datetime. Also note that this property is by default true, so when using encrypted time columns, you will have to set it to false. Otherwise the driver will throw as exception. The SQLServerConnection class has two methods, starting with version 6.0 of the driver to configure the value of this property programmatically:
 
* public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

For more information on this property visit [Configuring How java.sql.Time Values are Sent to the Server](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx). 

## See Also  
 [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/library/mt163865.aspx)  
  
  