
## Functions

### Q1

You develop an Azure function that connects to a SQL database. The function is instrumented by using Application Insights.
You need to view the full SQL query text when inspecting the Dependency tab in Application Insights.
Which two settings in the host.json file should you use? Each correct answer presents part of the solution.
Select all answers that apply.

- "enableDependencyTracking": true

- "dependencyTrackingOptions": { "enableSqlCommandTextInstrumentation": true },

- "enablePerformanceCountersCollection": true

- "logLevel": { "default": "Verbose" }


### Q2

You are developing an Azure Functions app that will be deployed to a Dedicated plan.
When there is a resource shortage in the app, it must send a “429 Too Busy” response.
You need to apply the appropriate configuration to all functions in a Azure Functions app instance.
Which configuration should you set?
Select only one answer.

*- dynamicThrottlesEnabled in the host.json file

- bindings section in the function.json file

- maxOutstandingRequests in the host.json file

- maxConcurrentRequests in the function.json file

### Q3

You manage an Azure App Service Functions app named app1 and a storage account named account1.
You have the following requirements:
	App1 should access account1 without managing credentials.
	The service principal associated with app1 cannot be explicitly deleted.
	You need to configure a security principal for app1.

Which security principal should you use?
Select only one answer.

- application

*- system-assigned managed identity

- user-assigned managed identity

- legacy

## Auth

### Q1

You deploy a .NET web application to an on-premises web server. You plan to use Application Insights to monitor the web application’s performance.
You need to allow the web application to upload its telemetry to Application Insights.
Which authorization method should you use?
Select only one answer.

- access key
- instrumentation key
- system-assigned managed identity
- user-assigned managed identity


### Q2

You develop an application. The application will be accessed by a supplier.

The supplier requires a shared access signature (SAS) to access Azure services in your company’s subscription.

You need to secure the SAS.

Which three actions should you take? Each correct answer presents a complete solution.

Select all answers that apply.

*- Always use HTTPS.
-  Grant permission to multiple resources.
*- Use Azure Monitor and Azure Storage logs to monitor the application.
*- Define a stored access policy for a service SAS.
- Set a long expiration time

This item tests the candidate’s knowledge of creating and implementing shared access signatures (SAS).

The recommendation of always using HTTPS is valid and should be followed. Azure Monitor and storage analytics 
logging should be used to observe any spike in these types of authorization failures. Stored access policies
 will give the option to revoke permissions for a service SAS without having to regenerate the storage account keys.
 A security best practice is to provide a user with the minimum required privileges. It is best to use 
near-term expiration times on an ad-hoc SAS service or account SAS so that even if a SAS is compromised 
it is valid only for a short time.


### Q3

You develop a multitenant web application named App1. You plan to register App1 with multiple Microsoft Entra ID tenants.

You need to identify the relationship between the application objects and security principals associated with App1.

Which relationship should you identify?

Select only one answer.

-  App1 will have multiple application objects and multiple service principals.
-  App1 will have multiple application objects and a single service principal.
*- App1 will have a single application object and multiple service principals.
-  App1 will have a single application object and a single service principal.

This item tests the candidate’s knowledge of configuring authentication of multitenant applications, which is a common scenario when implementing authentication.

App1 will have a single application object and multiple service principals. App1 will not have multiple application objects. multiple application objects and a single service principal., or a single service principal.


### Q4

You need to generate a shared access signature token that grants the Read permission to a blob container.
Which code segment should you use?

- ex1
BlobSasBuilder sasBuilder = new BlobSasBuilder() { BlobContainerName = containerClient.Name, Resource = "b" }; 
sasBuilder.ExpiresOn = DateTimeOffset.UtcNow.AddHours(1); sasBuilder.SetPermissions(BlobContainerSasPermissions.Read); 
Uri sasUri = containerClient.GenerateSasUri(sasBuilder);

*- ex2
BlobSasBuilder sasBuilder = new BlobSasBuilder() { BlobContainerName = containerClient.Name, Resource = "c" }; 
sasBuilder.ExpiresOn = DateTimeOffset.UtcNow.AddHours(1); sasBuilder.SetPermissions(BlobContainerSasPermissions.Read); 
Uri sasUri = containerClient.GenerateSasUri(sasBuilder);

- ex3
BlobSasBuilder sasBuilder = new BlobSasBuilder() { BlobContainerName = containerClient.Name, Resource = “c” }; 
sasBuilder.ExpiresOn = DateTimeOffset.UtcNow.AddHours(1); sasBuilder.SetPermissions(BlobContainerSasPermissions.Create); 
Uri sasUri = containerClient.GenerateSasUri(sasBuilder);

- ex4
BlobSasBuilder sasBuilder = new BlobSasBuilder() { BlobContainerName = containerClient.Name, Resource = "b" }; 
sasBuilder.ExpiresOn = DateTimeOffset.UtcNow.AddHours(1); sasBuilder.SetPermissions(BlobContainerSasPermissions.Create); 
Uri sasUri = containerClient.GenerateSasUri(sasBuilder);

This item tests the candidate’s knowledge of creating and implementing shared access signatures.

The code segment that includes Resource = "c" and sasBuilder.SetPermissions(BlobContainerSasPermissions.Read); 
will generate the shared access signatures token that grants the Read permission to a blob container. The code 
segment that includes resource = ‘b’ will generate a shared access signatures token at the blob level. The code 
segments that include sasBuilder.SetPermissions(BlobContainerSasPermissions.Create); will generate a shared access 
signatures token with the Create permission at the blob level.


### Q5

You manage an Azure App Service Functions app named app1 and a storage account named account1.
You have the following requirements:
	App1 should access account1 without managing credentials.
	The service principal associated with app1 cannot be explicitly deleted.
	You need to configure a security principal for app1.

Which security principal should you use?

Select only one answer.

-  application
*- system-assigned managed identity
-  user-assigned managed identity
-  legacy

This item tests the candidate’s knowledge of implementing managed identities, which is part of implementing secure cloud solutions.

Managed identities for Azure resources eliminate the need to manage credentials in code. A system-assigned managed identity is restricted 
to one per resource and is tied to the lifecycle of the resource. Once enabled for app1, it will automatically create a service principal 
without the need to manage credentials and cannot be explicitly deleted.

A Microsoft Entra ID application is defined by its one and only application object, which resides in the Microsoft Entra ID tenant 
where the application was registered (known as the application's home tenant). It cannot be used by app1 to access a storage account 
without managing credentials. A user-assigned managed identity can be created and assigned to one or more instances of an Azure service. 
Once enabled for app1, a user-assigned managed identity will automatically create a service principal without the need to manage but will 
need to be explicitly deleted. The legacy service principal represents a legacy app, which is an app created before app registrations 
were introduced or an app created through legacy experiences. The legacy service principal cannot be used to access a storage 
account without managing credentials.


### Q6

You have an Azure App Configuration instance named AppConfig1 and an Azure key vault named KeyVault1.
You plan to encrypt data stored in AppConfig1 by using your own key stored in KeyVault1.
You need to grant permissions in KeyVault1 to the identity assigned to AppConfig1.
Which three key-specific permissions should you use? Each correct answer presents part of the solution.

Select all answers that apply.

DECRYPT
ENCRYPT
*- GET
*- UNWRAP
*- WRAP

This item tests the candidate’s knowledge of implementing bring your own key encryption scenarios, which is an essential part of implementing secure cloud solutions.

To use the custom key stored in KeyVault1, the identity assigned to AppConfig1 needs to have GET, WRAP, and UNWRAP permissions to the custom key. 
The DECRYPT and ENCRYPT permissions are not required to use the custom key stored in KeyVault1 in this scenario.


### Q7

You manage an Azure App Service web app named app1. App1 is registered as a multi-tenant application in a 
Microsoft Entra ID tenant named tenant1. You need to grant app1 the permission to access the Microsoft Graph API 
in tenant1. Which service principal should you use?

*- application
- user-assigned managed identity
- system-assigned managed identity
- legacy

This item tests the candidate’s knowledge of accessing user data from Microsoft Graph, which is part of 
implementing user authentication and authorization.

A Microsoft Entra ID application is defined by its one and only application object, which resides in the 
Microsoft Entra ID tenant where the application was registered (known as the application's home tenant). 
The application service principal is used to configure permission for app1 in tenant1 to access the 
Microsoft Graph API. 

The legacy service principal is a legacy app, which is an app created before app registrations were introduced 
or an app created through legacy experiences. Managed identities eliminate 
the need to manage credentials in code. 

A system-assigned managed identity is restricted to one per resource and is tied to the lifecycle of the 
resource. Managed identities for Azure resources eliminate the need to manage credentials in code. 

A user-assigned managed identity can be created and assigned to one or more instances of an Azure service. 

The legacy, system-assigned managed identity, and user-assigned managed identity cannot be used to assign 
permission for app1 in tenant1 to access the Microsoft Graph API.