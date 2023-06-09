# Hub

If you haven't yet, clone the repo and cd to the appropriate folder
``` bash
git clone https://github.com/Azure/ACA-Landing-Zone-Accelerator
```

The following will be created:

* Resource Group for Hub Networking
* Hub VNET
* Azure Bastion Host (Optional)
* Windows or Linux Virtual Machine (Optional)

![Hub](./media/hub.png)

Review the `deploy.hub.parameters.jsonc` file and update the parameter values if required according to your needs. Pay attentions to VNET address prefixes and subnets so it doesn't overlap Spoke VNET in further steps. Also, please pay attention to update Subnet prefix for ACA environment in Spoke VNET in the further steps to be planned and update in this file.

> TODO: Add VM AAD joined (needs bastion Standard)

Note: `deploy.hub.parameters.jsonc` file contains the username and password for the virtual machine. These can be changed in the parameters file for the VM, however these are the default values:

```
Username: azureuser
Password: Password123
```

Once the files are updated, deploy using az cli or Az PowerShell.

## [CLI](#tab/CLI)

```azurecli
az deployment sub create -n <DEPLOYMENT_NAME> -l <LOCATION> -f deploy.hub.bicep -p deploy.hub.parameters.jsonc
```

 Where `<LOCATION>` is the location where you want to deploy the landing zone and `<DEPLOYMENT_NAME>` is the name of the deployment.

## [PowerShell](#tab/PowerShell)

```azurepowershell
New-AzSubscriptionDeployment -TemplateFile deploy.hub.bicep -TemplateParameterFile deploy.hub.parameters.jsonc -Location "<LOCATION>" -Name <DEPLOYMENT_NAME>
```

Where `<LOCATION>` is the location where you want to deploy the landing zone and `<DEPLOYMENT_NAME>` is the name of the deployment.

:arrow_forward: [Spoke](../02-spoke)
