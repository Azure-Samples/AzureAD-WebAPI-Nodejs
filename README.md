---
services: active-directory
platforms: nodejs
author: brandwe
---

# Securing a web API with Azure AD

This Node.js server will give you a quick and easy way to set up a REST API Service using the OAuth2 protocol. Then this service is integrated with Azure Active Directory for API protection. The sample server included in the download is designed to run on any platform.

This REST API server is built using Restify and MongoDB with the following features:

* A node.js server running an REST API interface with JSON using MongoDB as persistent storage
* REST APIs leveraging OAuth2 API protection for endpoints using Azure Active Directory

We've released all of the source code for this example in GitHub under an Apache 2.0 license, so feel free to clone (or even better, fork!) and provide feedback on the forums.


## Quick Start

>[!Note] If you want to run this sample on **Azure Government**, navigate to the "Azure Government Deviations" section at the bottom of this page.
>
>
>

Getting started with the sample is easy. It is configured to run out of the box with minimal setup.

### Step 1: Register a Azure AD Tenant

To use this sample you will need a Azure Active Directory Tenant. If you're not sure what a tenant is or how you would get one, read [What is an Azure AD tenant](http://technet.microsoft.com/library/jj573650.aspx)? or [Sign up for Azure as an organization](http://azure.microsoft.com/en-us/documentation/articles/sign-up-organization/). These docs should get you started on your way to using Azure AD.

### Step 2: Register your Web API with your Azure AD Tenant

After you get your Azure AD tenant, add this sample app to your tenant so you can use it to protect your API endpoints. If you need help with this step, see: [Register the REST API Service Azure Active Directory](https://github.com/AzureADSamples/WebAPI-Nodejs/wiki/Setup-Windows-Azure-AD)

### Step 3: Download node.js for your platform
To successfully use this sample, you need a working installation of Node.js.

Install Node.js from [http://nodejs.org](http://nodejs.org).

### Step 4: Install MongoDB on to your platform

To successfully use this sample, you must have a working installation of MongoDB. We will use MongoDB to make our REST API persistent across server instances.

Install MongoDB from [http://mongodb.org](http://www.mongodb.org).

**NOTE:** This walkthrough assumes that you use the default installation and server endpoints for MongoDB, which at the time of this writing is: mongodb://localhost. This should work locally without any configuration changes if you run this sample on the same machine as you've installed and ran mongodb.


### Step 5: Download the Sample application and modules

Next, clone the sample repo and install the NPM.

From your shell or command line:

* `$ git clone https://github.com/Azure-Samples/active-directory-node-webapi.git`
* `$ cd node-server`
* `$ npm install`

### Step 6: Configure your server using config.js

You will need to update the sample to use your values for the metadata endpoint.

**NOTE:** If you wish to accept multiple tenants for this app, you'll want to use the *common* endpoint and you'll need to pass the `issuer:` and `audience:` value if you wish to validate that as well.

### Step 7: Run the application


* `$ cd node-server	`
* `$ node app.js`

**Is the server output hard to understand?:** We use `bunyan` for logging in this sample. The console won't make much sense to you unless you also install bunyan and run the server like above but pipe it through the bunyan binary:

* `$ npm install -g bunyan`
* `$ node app.js | bunyan`

### You're done!

You will have a server successfully running on `http://localhost:3000`. Your REST / JSON API Endpoint will be `http://localhost:3000/tasks`

## Azure Government Deviations

In order to run this sample on Azure Government you can follow through the steps above with a few variations:

- Step 2: 
   - You must register this sample for your AAD Tenant in Azure Government by following Step 2 above in the [Azure Government portal](https://portal.azure.us). 
- Step 3: 
    - Navigate to the `node-server` folder and open the `config.js` file. The `IdentityMetadata` property should end with `.us`. The common `IdentityMetadata` property should be: `https://login.microsoftonline.us/common/.well-known/openid-configuration`. 
    
Once those changes have been accounted for, you should be able to run this sample on Azure Government.  

### Acknowledgements

We would like to acknowledge the folks who own/contribute to the following projects for their support of Azure Active Directory and their libraries that were used to build this sample. In places where we forked these libraries to add additional functionality, we ensured that the chain of forking remains intact so you can navigate back to the original package. Working with such great partners in the open source community clearly illustrates what open collaboration can accomplish. Thank you!


- [MongoDB](http://www.mongodb.org) - MongoDB (from "humongous") is an open-source document database, and the leading NoSQL database. Written in C++
- [Restify](http://mcavage.me/node-restify/) - Restify is a node.js module built specifically to enable you to build correct REST web services. ``` node-restify```
- [Restify-OAuth2](https://github.com/domenic/restify-oauth2) - This package provides a very simple OAuth 2.0 endpoint for the Restify framework. ``` restify-oauth2```
- [node-jwt-simple](https://github.com/hokaccha/node-jwt-simple) - Library for parsing JSON Web Tokens (JWT) ```node-jwt-simple```
- [http-bearer-strategy](https://github.com/jaredhanson/passport-http-bearer) - HTTP Bearer authentication strategy for Passport and Node.js.




## About The Code

Code hosted on GitHub under Apache 2.0 license
