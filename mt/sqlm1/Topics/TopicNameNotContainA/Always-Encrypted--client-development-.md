---
title: Always Encrypted (client development)
ms.custom: 
  - SQL2016_New_Updated
ms.devlang: 
  - CSharp
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
---
# Always Encrypted (client development)
  Always Encrypted allows clients to encrypt sensitive data inside client applications and never reveal the encryption keys to SQL Server. An Always Encrypted enabled driver installed on the client computer achieves this by automatically encrypting and decrypting sensitive data in the SQL Server client application. The driver encrypts the data in sensitive columns before passing the data to SQL Server, and automatically rewrites queries so that the semantics to the application are preserved. Similarly, the driver transparently decrypts data stored in encrypted database columns that are contained in query results. For more information, see [Always Encrypted &#40;Database Engine&#41;](../Topic/Always%20Encrypted%20\(Database%20Engine\).md).  
  
## Developing client applications for accessing Always Encrypted data  
 Querying a database using Always Encrypted from a client application requires minimal development effort. The following summarizes the prerequisites and steps you must take for your application to read and write Always Encrypted data. For additional information, see the [Always Encrypted blog](http://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/).  
  
 For an end\-to\-end walkthrough that shows how to  configure Always Encrypted with the wizard and use it in a client application, see [SQL Database tutorial: Protect sensitive data with Always Encrypted](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/).  
  
### Prerequisites  
  
-   Configure the server by following the directions in the **Getting Started with Always Encrypted** section of the [Always Encrypted &#40;Database Engine&#41;](../Topic/Always%20Encrypted%20\(Database%20Engine\).md) topic.  
  
-   Install **.Net Framework version 4.6 or higher** on the client computer. For details, see [.NET Framework 4.6](https://msdn.microsoft.com/library/w0x726c2.aspx).  
  
    > [!NOTE]  
    >  **.NET Framework version 4.6.1 RC** is required when using Always Encrypted with the [SqlColumnEncryptionCngProvider Class](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx), [SqlColumnEncryptionCspProvider Class](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncspprovider.aspx), or the [AllowEncryptedValueModifications](https://msdn.microsoft.com/library/bedk11dz.aspx) bulk copy option.  
  
### Set up the client application  
  
-   The client application must be configured to have access to a key store containing a column master key protecting the data the application is going to access. For information about master keys, see [Always Encrypted &#40;Database Engine&#41;](../Topic/Always%20Encrypted%20\(Database%20Engine\).md).  
  
### Enabling Always Encrypted for a client connection  
 Modify the connection string in your client application by adding the `Column Encryption Setting=enabled` parameter to the connection string.  
  
 The following is an example of a connection string that enables Always Encrypted:  
  
```c#  
string connectionString = "Data Source=server63; Integrated Security=true; Column Encryption Setting=enabled";  
```  
  
### Inserting data example  
 Insert data into encrypted columns by passing the values in [SqlParameter](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.aspx) objects.  
  
 The following example assumes the `Name` and `PersonalId` columns are configured as Always Encrypted columns on the server. The application passes plaintext values in **SqlParameter** objects to the driver. The driver encrypts these values and then passes the encrypted values to the server.  
  
```c#  
using (SqlCommand cmd = new SqlCommand("usp_add_customer", connection))  
{  
   cmd.CommandType = CommandType.StoredProcedure;  
  
   SqlParameter Name = new SqlParameter("@Name", System.Data.SqlDbType.NVarChar, 60);  
   Name.Value = "Jim Gray";  
  
   cmd.Parameters.Add(Name);  
  
   SqlParameter PersonalId = new SqlParameter("@PersonalId", System.Data.SqlDbType.VarChar, 11);  
   PersonalId.Value = "111-22-3333";  
  
   cmd.Parameters.Add(PersonalId);  
   cmd.ExecuteNonQuery();  
}  
  
```  
  
 For reference, the `usp_add_customer` stored procedure is defined as follows:  
  
```sql  
CREATE PROCEDURE usp_add_customer  
@Name NVARCHAR(60)  
, @PersonalId VARCHAR(11)   
AS   
INSERT INTO Customers  
VALUES(@Name, @PersonalId)  
  
```  
  
 The server receives the following command; no plaintext data is available to the server.  
  
```sql  
EXEC usp_add_customer   
@Name=0x0198E1D94EF8FBBAF…,   
@PersonalId=0x019824462E3CB8BA4…  
```  
  
### Fetching data example  
 The following example demonstrates filtering data based on encrypted values.  
  
> [!NOTE]  
>  Queries can perform equality comparisons on columns if they are encrypted using deterministic encryption. For more information, see **Selecting Deterministic or Randomized encryption** section of the [Always Encrypted &#40;Database Engine&#41;](../Topic/Always%20Encrypted%20\(Database%20Engine\).md) topic.  
  
```c#  
using (SqlCommand cmd = new SqlCommand("SELECT Name FROM Customers WHERE PersonalId = @PersonalId", connection))  
{  
   SqlParameter PersonalId = new SqlParameter("@PersonalId", System.Data.SqlDbType.VarChar, 11);  
   PersonalId.Value = "111-22-3333";  
  
   cmd.Parameters.Add(PersonalId);  
   cmd.ExecuteReader();  
}  
  
```  
  
 The following represents the query that the server receives. Once again, no plaintext values are available to the server, and deterministic encryption allows the equality operator to locate and return the matching record. Assuming we are using the same data as inserted above the query result is decrypted and the client receives the record for 'Jim Gray'.  
  
```tsql  
EXEC sp_executesql  
N'SELECT * FROM Customers WHERE PersonalId = @PersonalId'  
, @params = N'@PersonalId VARCHAR(11)', @PersonalId=0x019824462E3CB8BA4…  
```  
  
### Controlling the performance impact when querying encrypted columns  
 If Always Encrypted has been enabled in the connection string, by default the driver will call [sys.sp\_describe\_parameter\_encryption](../Topic/sp_describe_parameter_encryption%20\(Transact-SQL\).md) for each query containing **SqlParameter** objects, passing the encrypted query statement \(with encrypted parameter values\) to SQL Server. **sys.sp\_describe\_parameter\_encryption** analyzes the query statement and for each parameter that needs to be encrypted, it returns the encryption\-related information that will allow the driver to encrypt parameter values. The above behavior ensures a high\-level of transparency to the client application. The application \(and the application developer\) do not need to be aware of which queries access encrypted columns, as long as values are passed to the driver in **SqlParameter** objects.  
  
 The **.NET Framework Provider for SQL Server** allows you to control the above behavior for individual queries using [SqlCommand](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommand.aspx) and [SqlCommandColumnEncryptionSetting](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommandcolumnencryptionsetting.aspx). By doing so, you can optimize the performance of your queries, at the price of reduced transparency. Here are some useful guidelines:  
  
-   If most queries a client application sends over a database connection access encrypted columns:  
  
    -   Set the **Column Encryption Setting** connection string keyword to **Enabled**.  
  
    -   Set **SqlCommandColumnEncryptionSetting.Disabled** for individual queries that do not access any encrypted columns.  
  
    -   Set **SqlCommandColumnEncryptionSetting.ResultSet** for individual queries that do not have any parameters requiring encryption, but retrieve data from encrypted columns.  
  
-   If most queries a client application sends over a database connection do not access encrypted columns:  
  
    -   Set the **Column Encryption Setting** connection string keyword to **Disabled**.  
  
    -   Set **SqlCommandColumnEncryptionSetting.Enabled** for individual queries that have any parameters that need to be encrypted.  
  
    -   Set **SqlCommandColumnEncryptionSetting.ResultSet** for queries that do not have any parameters requiring encryption, but retrieve data from encrypted columns.  
  
 See the example below for details:  
  
```c#  
string connectionString = "Data Source=server63; Integrated Security=true; Column Encryption Setting=enabled";  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
   conn.Open();  
   // This query does not send or retrieve encrypted data.  
   // Disable Always Encrypted to improve performance.  
   // SqlCommandColumnEncryptionSetting has the following values:  
   //   UseConnectionSetting (default), Disabled, Enabled, ResultSetOnly.  
   using (SqlCommand cmd = new SqlCommand("SELECT COUNT(*) FROM Customers", connection, null,   
   SqlCommandColumnEncryptionSetting.Disabled)  
   {  
     //...  
   }  
   // This query does not send any encrypted parameters (it only retrieves encrypted data).  
   // Disable fetching encryption metadata for parameters to optimize for performance.  
   using (SqlCommand cmd = new SqlCommand("SELECT PersonalId FROM Customers", connection, null,   
   SqlCommandColumnEncryptionSetting.ResultSetOnly)  
   {  
     //...  
   }  
}  
  
```  
  
### Creating and registering a custom Column Master Key Store Provider  
 Information the driver receives from SQL Server for query parameters which need to be encrypted, and for query results which need to be decrypted, includes:  
  
-   An encrypted value of a column encryption key, which should be used to encrypt or decrypt a parameter or a result.  
  
-   The name of a key store provider that encapsulates a key store containing the column master key which was used to encrypt the column encryption key.  
  
-   A key path that specifies the location of the column master key in the key store.  
  
-   The name of the algorithm that was used to encrypt the column encryption key.  
  
 The driver uses the above information to use the key store provider implementation to decrypt the retrieved encrypted value of the column encryption key, which is subsequently used to either encrypt a query parameter or to decrypt a query result.  
  
 The driver comes with implementations for three system providers:  
  
-   **SqlColumnEncryptionCertificateStoreProvider** which can be used to store column master keys in Windows Certificate Store.  
  
-   **SqlColumnEncryptionCngProvider** which can be used to store column master keys using the  Microsoft Cryptography API: Next Generation \(CNG\). *Requires .NET Framework version 4.6.1 RC*.  
  
-   **SqlColumnEncryptionCspProvider** which can be used to store column master keys using the Microsoft CAPI based Cryptographic Service Providers \(CSP\). *Requires .NET Framework version 4.6.1 RC*.  
  
 You can use a custom key store provider by extending the **SqlColumnEncryptionKeyStoreProvider** class and registering it using the **SqlConnection.RegisterColumnEncryptionKeyStoreProviders\(\)** method.  
For details, see the example below:  
  
```c#  
public class MyCustomKeyStoreProvider: SqlColumnEncryptionKeyStoreProvider  
{  
   public byte[]EncryptColumnEncryptionKey(string masterKeyPath, string encryptionAlgorithm, byte[] columnEncryptionKey)  
   {  
      // Logic for encrypting the CEK using the specified Master Key and algorithm.  
   }  
   public byte[]DecryptColumnEncryptionKey(string masterKeyPath, string encryptionAlgorithm, byte[] EncryptedColumnEncryptionKey)  
   {  
      // Logic for decrypting the CEK using the specified Master Key and algorithm.  
   }  
}  
  
class Program  
{  
   static void Main()  
   {  
      MyCustomKeyStoreProvider customProvider = new MyCustomKeyStoreProvider();  
      Dictionary<string, SqlColumnEncryptionKeyStoreProvider> providers =  
         new Dictionary<string, SqlColumnEncryptionKeyStoreProvider>();  
      providers.add('MY_CUSTOM_STORE', customProvider);  
      conn.RegisterColumnEncryptionKeyStoreProviders(providers);  
      . . .  
   }  
}  
  
```  
  
> [!NOTE]  
>  Any column master key stored in a key store must be defined in the database using [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20COLUMN%20MASTER%20KEY%20\(Transact-SQL\).md). The key store provider name in the definition of the column master key must match the provider name registered in the client application.  
  
### Always Encrypted API reference  
 There are several new additions and modifications to the [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) namespace for use in client applications that use Always Encrypted.  
  
 These updates are available in .NET Framework 4.6 and higher.  
**Namespace:**[System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx)  
**Assembly:** System.Data \(in System.Data.dll\)  
  
|Name|Description|  
|----------|-----------------|  
|[SqlColumnEncryptionCertificateStoreProvider Class](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncertificatestoreprovider.aspx)|A key store provider for Windows Certificate Store.|  
|[SqlColumnEncryptionCngProvider Class](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx)|A key store provider for Microsoft Cryptography API: Next Generation \(CNG\).|  
|[SqlColumnEncryptionCspProvider Class](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncspprovider.aspx)|A key store provider for Microsoft CAPI based Cryptographic Service Providers \(CSP\).|  
|[SqlColumnEncryptionKeyStoreProvider Class](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptionkeystoreprovider.aspx)|Base class of the key store providers.|  
|[SqlCommandColumnEncryptionSetting Enumeration](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommandcolumnencryptionsetting.aspx)|Settings to enable encryption and decryption for a database connection.|  
|[SqlConnectionColumnEncryptionSetting Enumeration](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnectioncolumnencryptionsetting.aspx)|Settings to control the behavior of Always Encrypted for individual queries.|  
|[SqlConnection.ColumnEncryptionTrustedMasterKeyPaths Property](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptiontrustedmasterkeypaths.aspx)|Allows you to set a list of trusted key paths for a database server. If while processing an application query the driver receives a key path that is not on the list, the query will fail. This property provides additional protection against security attacks that involve a compromised SQL Server providing fake key paths, which may lead to leaking key store credentials.|  
|[SqlConnection.RegisterColumnEncryptionKeyStoreProviders Method](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.registercolumnencryptionkeystoreproviders.aspx)|Allows you to register custom key store providers. It is a dictionary that maps key store provider names to key store provider implementations.|  
|[SqlCommand Constructor \(String, SqlConnection, SqlTransaction, SqlCommandColumnEncryptionSetting\)](https://msdn.microsoft.com/library/dn956511\(v=vs.110\).aspx)|Enables you to control the behavior of Always Encrypted for individual queries.|  
|[SqlParameter.ForceColumnEncryption Property](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.forcecolumnencryption.aspx)|Enforces encryption of a parameter. If SQL Server informs the driver that the parameter does not need to be encrypted, the query using the parameter will fail. This property provides additional protection against security attacks that involve a compromised SQL Server providing incorrect encryption metadata to the client, which may lead to data disclosure.|  
|New [connection string](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx) keyword: `Column Encryption Setting=enabled`|Enables or disables Always Encrypted functionality for the connection.|  
  
### Code Examples  
 The following code snippets show how to encrypt data, generate an encrypted column encryption key, and how to bulk insert encrypted data using SqlBulkCopy.  
  
 **Transparently encrypt sensitive data**  
  
 In the following example, simply by using **Use Column Encryption\=true** the web page code will transparently encrypt the sensitive data received by the user input and stores in SQL Server in encrypted form. Please note that the asymmetric key pair can be stored either in a CSP provider and CNG key store provider. Usage of DecryptColumnEncryptionKey is transparent to the application as it called automatically by the ADO.NET layer.  
  
```  
protected void Add_Employee(object sender, EventArgs e)   
{   
    // Open a connection to SQL Server   
string dbConn = "Data Source=my_srv;Initial Catalog=HRDB;Integrated Security=True;Use Column Encryption=true;";   
    SqlConnection sqlConnection = new SqlConnection(dbConn);   
    sqlConnection.Open();   
  
    // Set the traceflat   
  
    using (SqlCommand sqlCommand1 = new SqlCommand(@"DBCC TRACEON (106)", sqlConnection))   
    {   
        sqlCommand1.ExecuteNonQuery();   
    }   
  
     // Open a SqlCommand Object   
    string sqlStatement = @"insert into Employee (employee_id, employee_name, employee_salary, employee_team) values (@EmpId, @EmpName, @EmpSalary, @EmpTeam)";   
    SqlCommand sqlCommand = new SqlCommand(sqlStatement, sqlConnection);   
    SqlParameter id = new SqlParameter(@"@EmpId", System.Data.SqlDbType.Int, 0, System.Data.ParameterDirection.Input, false, 0, 0, null, System.Data.DataRowVersion.Current, Employee_Id.Text);   
    SqlParameter name = new SqlParameter(@"@EmpName", System.Data.SqlDbType.NVarChar, 150, System.Data.ParameterDirection.Input, false, 0, 0, null, System.Data.DataRowVersion.Current, Employee_Name.Text);   
    SqlParameter salary = new SqlParameter(@"@EmpSalary", System.Data.SqlDbType.Int, 0, System.Data.ParameterDirection.Input, false, 0, 0, null, System.Data.DataRowVersion.Current, Employee_Salary.Text);   
    SqlParameter team = new SqlParameter(@"@EmpTeam", System.Data.SqlDbType.NVarChar, 150, System.Data.ParameterDirection.Input, false, 0, 0, null, System.Data.DataRowVersion.Current, Employee_Team.Text);   
  
    sqlCommand.Parameters.Add(id);   
    sqlCommand.Parameters.Add(name);   
    sqlCommand.Parameters.Add(salary);   
    sqlCommand.Parameters.Add(team);   
  
    sqlCommand.ExecuteNonQuery();   
  
    // Close the database objects   
    sqlConnection.Close();   
  
    Result.Text = string.Format(@"Successfully added employee record for {0}", Employee_Name.Text);   
}  
```  
  
 **Generate an encrypted column encryption key**  
  
 In the following example, SqlColumnEncryptionCspProvider.EncryptColumnEncryptionKey and SqlColumnEncryptionCngProvider.EncryptColumnEncryptionKey are used to generate encrypted column encryption keys using the corresponding CSP provider name and CNG key store provider names and key identifiers.  
  
```  
internal static byte[] GetEncryptedCEKByCsp()   
{  
    const string ProviderName = "nCipher Enhanced RSA and AES Cryptographic Provider";   
    const string KeyName = "HrWebAlwaysEncryptedKey";   
  
    SqlColumnEncryptionCspProvider cspProvider = new SqlColumnEncryptionCspProvider();   
    byte[] columnEncryptionKey = GenerateRandomBytes(32);   
    string keyPath = String.Format(@"{0}\{1}", ProviderName, KeyName);   
    return cspProvider.EncryptColumnEncryptionKey(keyPath, @"RSA_OAEP", columnEncryptionKey);   
}   
  
internal static byte[] GetEncryptedCEKByCng()   
{  
    const string ProviderName = "nCipher Security World Key Storage Provider";   
    const string KeyName = "HrWebAlwaysEncryptedKey";   
    SqlColumnEncryptionCngProvider cspProvider = new SqlColumnEncryptionCngProvider();   
    byte[] columnEncryptionKey = GenerateRandomBytes(32);   
    string keyPath = String.Format(@"{0}\{1}", ProviderName, KeyName);   
    return cspProvider.EncryptColumnEncryptionKey(keyPath, @"RSA_OAEP", columnEncryptionKey);   
}   
```  
  
 **Direct inserts using SqlBulkCopy**  
  
 In the following example we use SqlBulkCopy class to transfer data from one table to another. Both tables are encrypted with the same encryption key. However, the code assumes that the client machine doesn’t have encryption keys.   
*Requires .NET Framework version 4.6.1 RC*.  
  
```  
public void CopyTablesUsingBulk (string sourceTable, string targetTable)   
{   
     using (SqlConnection connSource = new SqlConnection("Data Source=****;Initial Catalog=DBName;Integrated Security=True;Use Column Encryption=false;"))   
     using (SqlCommand cmd = new SqlCommand(string.Format("SELECT c1, c2 FROM {0}", sourceTable), connSource))   
     using (SqlDataReader reader = cmd.ExecuteReader())   
     {   
         SqlBulkCopy copy = new SqlBulkCopy("Data Source=****;Initial Catalog=DBName;Integrated Security=True;Use Column Encryption=false;",    
         SqlBulkCopyOptions.AllowEncryptedValueModifications);   
         copy.EnableStreaming = true;   
         copy.DestinationTableName = targetTable;   
         copy.WriteToServer(reader);   
         reader.Close();   
         copy.Close();   
         connSource.Close();   
     }   
}   
```  
  
## See Also  
 [Always Encrypted &#40;Database Engine&#41;](../Topic/Always%20Encrypted%20\(Database%20Engine\).md)   
 [Always Encrypted blog](http://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)  
  
  