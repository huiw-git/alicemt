---
title: Column Master Key Rotation (Always Encrypted)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5117b4fd-c8d3-48d5-87c9-756800769f31
---
# Column Master Key Rotation (Always Encrypted)
The rotation of a column master key is a process of replacing an existing column master key with the new column master key. After rotation, clean up your system by removing the values of column encryption keys, encrypted with the old column master key, from the database.  

Multiple column master keys allow for key rotation; periodically changing the key enhances security.

Typically, a column encryption key is created with just one encrypted value. When a column master key needs to be rotated (the current column master key needs to be replaced with the new column master key), you can add a new value of the column encryption key, encrypted with the new column master key. This will allow you to ensure client applications can access data encrypted with the column encryption key, while the new column master key is being made available to client applications. An Always Encrypted enabled driver in a client application that does not have access to the new master key, will be able to use the column encryption key value encrypted with the old column master key to access sensitive data.

  
## Step 1: Provision a new column master key  
1. x  
2. x  
  
## Step 2: Encrypt column encryption keys with the new column master key  
1. x  
2. x  
  
## Step 3: Configure your applications with the new column master key  



1. x  
2. x  
  
## Step 4: Clean up column encryption key values encrypted with the old column master key  
1. x  
2. x  
  
## Step 5: Archive your old column master key  
1. x  
2. x  
  
  
## Next Steps  
    
- Links  
  
## Additional Resources  
  
- Links  
- Links