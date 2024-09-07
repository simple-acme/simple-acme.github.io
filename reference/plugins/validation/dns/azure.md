---
layout: plugin
plugin: aa57b028-45fb-4aca-9cac-a63d94c76b4a
compatibility: All platforms
examples:
    - 
      name: Service Principal
      cmd: '‑‑azuretenantid 9741a4c9-0e0b-4f35-abbe-9af735194804 ‑‑azureclientid 2a32943f-e46b-469c-a42d-eb5c54bf798d ‑‑azuresecret ***** ‑‑azuresubscriptionid 6c1e8002-c547-4e93-a9b3-7163f51c380e ‑‑azureresourcegroupname myresourcegroup [‑‑azurehostedzone zone.example.com]'
    -
      name: Managaged Identity
      cmd: '‑‑azureusemsi ‑‑azuresubscriptionid 6c1e8002-c547-4e93-a9b3-7163f51c380e ‑‑azureresourcegroupname myresourcegroup [‑‑azurehostedzone zone.example.com]'
---
Create the record in Microsoft [Azure DNS](https://azure.microsoft.com/en-us/services/dns/).

## Authentication
There are two ways to authenticate with Azure:
#### Create an Entra ID Service Principal Account
Use the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest) to create a [Service Principal](https://docs.microsoft.com/en-us/cli/azure/create-an-azure-service-principal-azure-cli?view=azure-cli-latest)

You then need to give this Service Principal access to change DNS entries. In the Azure Portal:
* Go to `DNS Zones` > `sub.example.com` > `Access Control (IAM)`
* Click `Add`
* For Role, choose `DNS Zone Contributor`
* Assign access to `Entra ID user, group, or application`
* Select your Service Principal
* Click `Save`

#### Use a Managed Service Identity
More information [here](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview). Note that configuration can be different depending on your operating system version, e.g. [#1413](https://github.com/win-acme/win-acme/issues/1413).

### Configuring the plugin
During setup of the validation the program will ask several questions. 
Here is to answer them with information from the Azure Portal.

* `DNS Subscription ID`: DNS Zones > `sub.example.com` > `Subscription ID`
* `DNS Resource Group Name`: DNS zones > `sub.example.com` > `Resource Group`

Only when authenticating as a Service Principal:

* `Directory/tenant id`: Entra ID > Properties > `Directory ID`.
* `Application client id`: Entra ID > App registrations > [Service Principal] > `Application ID`.
* `Application client secret`: The password that was generated when you created the Service Principal.

### Resources
- [How to: Use Azure PowerShell to create a service principal with a certificate](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
- [DNS SDK](https://docs.microsoft.com/en-us/azure/dns/dns-sdk)