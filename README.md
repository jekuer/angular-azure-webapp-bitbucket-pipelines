
# Angular to Azure Webapp via Bitbucket Pipelines
Bitbucket Pipeline scripts to deploy Angular applications to Microsoft Azure Webapps.
For both, server side (with Node) and client side (with Apache) rendering versions.

  

## Setup

 1. Get a Microsoft Azure Subscription. 
 2. Create a Webapp (for the example, also create a "develop" slot in the webapp). 
 3. If you are using server side rendering (SSR), select a NodeJS runtime stack (mind that Azure will run the start script in your package.json on webapp start). If you are not using SSR, but rather client side rendering (CSR), I would recommend to go for the PHP7 stack, which will enable Apache as web server. 
 4. For the SSR version, you should define the Node server setup within your Angular app. For the CSR version, you should add an .htaccess file to your Angular app (check [https://github.com/jekuer/angular-ideal-htaccess](https://github.com/jekuer/angular-ideal-htaccess)). 
 5. Open Azure PowerShell and run "az ad sp create-for-rbac --name bitbucket-deployment-principal". 
 6. Note the values the call returns.
 7. Go to your Bitbucket repository, go for "settings" and hit "Repository variables" within the pipelines section.
 8. Create the following variables and use the previously gained values:
 * AZURE_APP_ID
 * AZURE_PASSWORD (make this one private)
 * AZURE_TENANT_ID
 9. Copy the bitbucket-pipelines.yml to your Angular project root.
 10. Adjust the file. 
 11. Push and see the magic happening!
