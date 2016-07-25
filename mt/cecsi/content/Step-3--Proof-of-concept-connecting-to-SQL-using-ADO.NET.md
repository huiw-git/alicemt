---
title: "Step 3: Proof of concept connecting to SQL using ADO.NET"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aebe3dc6-3ee4-4d11-8e43-5d32b3f91490
caps.latest.revision: 10
manager: jhubbard
---
# Step 3: Proof of concept connecting to SQL using ADO.NET
  
This example should be considered a proof of concept only. The sample code is simplified for clarity, and does not necessarily represent best practices recommended by Microsoft.  
  
## Step 1: Connect  
  
The method SqlConnection.Open is used to connect to your SQL database.  
  
  
  
```CSharp  
    using System;  // C# , ADO.NET  
    using C = System.Data.SqlClient; // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new C.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;Password=YOUR_PASSWORD_HERE;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
  
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    Press any key to finish...  
    ****/  
```  
  
  
  
## Step 2:  Execute a query  
  
The method SqlCommand.ExecuteReader:  
  
- Issues the SQL SELECT statement to the SQL system.  
- Returns an instance of SqlDataReader to provide access to the result rows.  
  
  
  
```CSharp  
    using System;  // C# , ADO.NET  
    using D = System.Data;           // System.Data.dll  
    using C = System.Data.SqlClient; // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new C.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;Password=YOUR_PASSWORD_HERE;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.SelectRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void SelectRows(C.SqlConnection connection)  
            {  
                using (var command = new C.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = D.CommandType.Text;  
                    command.CommandText = @"  
    SELECT  
        TOP 5  
            COUNT(soh.SalesOrderID) AS [OrderCount],  
            c.CustomerID,  
            c.CompanyName  
        FROM  
                            SalesLT.Customer         AS c  
            LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh  
                ON c.CustomerID = soh.CustomerID  
        GROUP BY  
            c.CustomerID,  
            c.CompanyName  
        ORDER BY  
            [OrderCount] DESC,  
            c.CompanyName; ";  
      
                    C.SqlDataReader reader = command.ExecuteReader();  
      
                    while (reader.Read())  
                    {  
                        Console.WriteLine("{0}\t{1}\t{2}",  
                            reader.GetInt32(0),  
                            reader.GetInt32(1),  
                            reader.GetString(2));  
                    }  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    1       29736   Action Bicycle Specialists  
    1       29638   Aerobic Exercise Company  
    1       29546   Bulk Discount Store  
    1       29741   Central Bicycle Specialists  
    1       29612   Channel Outlet  
    Press any key to finish...  
    ****/  
```  
  
  
  
## Step 3: Insert a row  
  
  
This example demonstrates how to:  
  
- Execute an SQL INSERT statement safely by passing parameters.  
  - Use of parameters protects against SQL injection attacks.  
- Retrieve the auto-generated value.  
  
  
  
```CSharp  
    using System;  // C# , ADO.NET  
    using D = System.Data;           // System.Data.dll  
    using C = System.Data.SqlClient; // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new C.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;Password=YOUR_PASSWORD_HERE;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.InsertRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void InsertRows(C.SqlConnection connection)  
            {  
                C.SqlParameter parameter;  
      
                using (var command = new C.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = D.CommandType.Text;  
                    command.CommandText = @"  
    INSERT INTO SalesLT.Product  
            (Name,  
            ProductNumber,  
            StandardCost,  
            ListPrice,  
            SellStartDate  
            )  
        OUTPUT  
            INSERTED.ProductID  
        VALUES  
            (@Name,  
            @ProductNumber,  
            @StandardCost,  
            @ListPrice,  
            CURRENT_TIMESTAMP  
            ); ";  
      
                    parameter = new C.SqlParameter("@Name", D.SqlDbType.NVarChar, 50);  
                    parameter.Value = "SQL Server Express 2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new C.SqlParameter("@ProductNumber", D.SqlDbType.NVarChar, 25);  
                    parameter.Value = "SQLEXPRESS2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new C.SqlParameter("@StandardCost", D.SqlDbType.Int);  
                    parameter.Value = 11;  
                    command.Parameters.Add(parameter);  
      
                    parameter = new C.SqlParameter("@ListPrice", D.SqlDbType.Int);  
                    parameter.Value = 12;  
                    command.Parameters.Add(parameter);  
      
                    int productId = (int)command.ExecuteScalar();  
                    Console.WriteLine("The generated ProductID = {0}.", productId);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    The generated ProductID = 1000.  
    Press any key to finish...  
    ****/  
```  
  
