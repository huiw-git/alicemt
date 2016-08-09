---
title: "Configure Dialog Security for Event Notifications"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12afbc84-2d2a-4452-935e-e1c70e8c53c1
caps.latest.revision: 24
manager: jhubbard
---
# Configure Dialog Security for Event Notifications
[!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] dialog security should be configured for event notifications that send messages to a service broker on a remote server. Dialog security must be manually configured according to the [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] dialog full-security model. The full-security model enables encryption and decryption of messages that are sent to and from remote servers. Although event notifications are sent in one direction, other messages, such as errors, are also returned in the opposite direction.  
  
## Configuring Dialog Security for Event Notifications  
 The process required to implement dialog security for event notification is described in the following steps. These steps include actions to take on both the source server and the target server. The source server is the server on which the event notification is being created. The target server is the server that receives the event notification message. You must complete the actions in each step for both the source server and the target server before you continue to the next step.  
  
> [!IMPORTANT]  
>  All certificates must be created with valid start and expiration dates.  
  
 **Step 1: Establish a TCP port number and target service name.**  
  
 Establish the TCP port on which both the source server and the target server will receive messages. You must also determine the name of the target service.  
  
 **Step 2: Configure encryption and certificate sharing for database-level authentication.**  
  
 Complete the following actions on both the source and target servers.  
  
|Source server|Target server|  
|-------------------|-------------------|  
|Choose or create a database to hold the event notification and master key.|Choose or create a database to hold the master key.|  
|If no master key exists for the source database, [create a master key](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76). A master key is required on both the source and target databases to help secure their respective certificates.|If no master key exists for the target database, create a master key.|  
|[Create a login](assetId:///eb737149-7c92-4552-946b-91085d8b1b01) and a corresponding [user](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80) for the source database.|Create a login and a corresponding user for the target database.|  
|[Create a certificate](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d) that is owned by the user of the source database.|Create a certificate that is owned by the user of the target database.|  
|[Back up the certificate](assetId:///509b9462-819b-4c45-baae-3d2d90d14a1c) to a file that can be accessed by the target server.|Back up the certificate to a file that can be accessed by the source server.|  
|[Create a user](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80), specifying the user of the target database, and WITHOUT LOGIN. This user will own the target database certificate to be created from the backup file. The user does not have to be mapped to a login, because the only purpose of this user is to own the target database certificate created in step 3 that follows.|Create a user, specifying the user of the source database, and WITHOUT LOGIN. This user will own the source database certificate to be created from the backup file. The user does not have to be mapped to a login, because the only purpose of this user is to own the source database certificate created in step 3 that follows.|  
  
 **Step 3: Share certificates and grant permissions for database-level authentication.**  
  
 Complete the following actions on both the source and target servers.  
  
|Source server|Target server|  
|-------------------|-------------------|  
|[Create a certificate](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d) from the backup file of the target certificate, specifying the target database user as the owner.|Create a certificate from the backup file of the source certificate, specifying the source database user as the owner.|  
|[Grant permission](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185) to create the event notification to the source database user. For more information about this permission, see [CREATE EVENT NOTIFICATION (Transact-SQL)](assetId:///dbbff0e8-9e25-4f12-a1ba-e12221d16ac2).|Grant REFERENCES permission to the target database user on the existing event notifications [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] contract: `http://schemas.microsoft.com/SQL/Notifications/PostEventNotification`.|  
|[Create a remote service binding](assetId:///4165c404-4d50-4063-9a6e-6e267d309376) to the target service and specify the credentials of the target database user. The remote service binding guarantees that the public key in the certificate owned by the source database user will authenticate messages that are sent to the target server.|[Grant](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185) CREATE QUEUE, CREATE SERVICE, and CREATE SCHEMA permissions to the target database user.|  
||If not already connected to the database as the target database user, do so now.|  
||[Create a queue](assetId:///fce80faf-2bdc-475d-8ca1-31438ed41fb0) to receive the event notification messages and [create a service](assetId:///fb804fa2-48eb-4878-a12f-4e0d5f4bc9e3) to deliver the messages.|  
||[Grant SEND permission](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185) on the target service to the source database user.|  
|Provide the service broker identifier of the source database to the target server. This identifier can be obtained by querying the **service_broker_guid** column of the [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view. For a server-level event notification, use the service broker identifier of **msdb**.|Provide the service broker identifier of the target database to the source server.|  
  
 **Step 4: Create routes and set up server-level authentication.**  
  
 Complete the following actions on both the source and target servers.  
  
|Source server|Target server|  
|-------------------|-------------------|  
|[Create a route](assetId:///7e695364-1a98-4cfd-8ebd-137ac5a425b3) to the target service, and specify the service broker identifier of the target database and the agreed-upon TCP port number.|Create a route to the source service, and specify the service broker identifier of the source database and the agreed-upon TCP port number. To specify the source service, use the following supplied service: `http://schemas.microsoft.com/SQL/Notifications/EventNotificationService`.|  
|Switch to the **master** database to configure server-level authentication.|Switch to the **master** database to configure server-level authentication.|  
|If no master key exists for the **master** database, [create a master key](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76).|If no master key exists for the **master** database, create a master key.|  
|[Create a certificate](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d) that authenticates the database.|Create a certificate that authenticates the database.|  
|[Back up the certificate](assetId:///509b9462-819b-4c45-baae-3d2d90d14a1c) to a file that can be accessed by the target server.|Back up the certificate to a file that can be accessed by the source server.|  
|[Create an endpoint](assetId:///6405e7ec-0b5b-4afd-9792-1bfa5a2491f6), and specify the agreed-upon TCP port number, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*), and the name of the authenticating certificate.|Create an endpoint, and specify the agreed-upon TCP port number, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*), and the name of the authenticating certificate.|  
|[Create a login](assetId:///eb737149-7c92-4552-946b-91085d8b1b01), and specify the login of the target server.|Create a login, and specify the login of the source server.|  
|[Grant CONNECT permission](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185) on the endpoint to the target authenticator login.|Grant CONNECT permission on the endpoint to the source authenticator login.|  
|[Create a user](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80), and specify the target authenticator login.|Create a user, and specify the source authenticator login.|  
  
 **Step 5: Share certificates for server-level authentication and create the event notification.**  
  
 Complete the following actions on both the source and target servers.  
  
|Source server|Target server|  
|-------------------|-------------------|  
|[Create a certificate](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d) from the backup file of the target certificate, specifying the target authenticator user as the owner.|Create a certificate from the backup file of the source certificate, specifying the source authenticator user as the owner.|  
|Switch to the source database on which to create the event notification, and if you are not already connected as the source database user, do so now.|Switch to the target database to receive event notification messages.|  
|[Create the event notification](assetId:///dbbff0e8-9e25-4f12-a1ba-e12221d16ac2), and specify the broker service and identifier of the target database.||  
  
## See Also  
 [GRANT](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185)   
 [BACKUP CERTIFICATE (Transact-SQL)](assetId:///509b9462-819b-4c45-baae-3d2d90d14a1c)   
 [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)   
 [Encryption Hierarchy](../../Topics/TopicNameNotContainA/Encryption-Hierarchy.md)   
 [Implement Event Notifications](../../Topics/TopicNameNotContainA/Implement-Event-Notifications.md)   
 [CREATE MASTER KEY (Transact-SQL)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76)   
 [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01)   
 [CREATE USER (Transact-SQL)](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80)   
 [CREATE CERTIFICATE (Transact-SQL)](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d)   
 [CREATE REMOTE SERVICE BINDING (Transact-SQL)](assetId:///4165c404-4d50-4063-9a6e-6e267d309376)   
 [GRANT (Transact-SQL)](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185)   
 [CREATE ROUTE (Transact-SQL)](assetId:///7e695364-1a98-4cfd-8ebd-137ac5a425b3)   
 [CREATE QUEUE (Transact-SQL)](assetId:///fce80faf-2bdc-475d-8ca1-31438ed41fb0)   
 [CREATE SERVICE (Transact-SQL)](assetId:///fb804fa2-48eb-4878-a12f-4e0d5f4bc9e3)   
 [CREATE ENDPOINT (Transact-SQL)](assetId:///6405e7ec-0b5b-4afd-9792-1bfa5a2491f6)   
 [CREATE EVENT NOTIFICATION (Transact-SQL)](assetId:///dbbff0e8-9e25-4f12-a1ba-e12221d16ac2)