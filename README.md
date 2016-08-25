# ScriptExecutionOrder
Uses Azure RM template dependencies to ensure script extension execution order for cases like setting up MariaDB clusters where scripts to install DB and create cluster has to complete in first VM before the script on second VM can start and so forth. The template shows the concept how this can be done. It uses first script extension as dependecy for second secript and so forth. This is defined by the variable scriptDependencies in the template

To use, replace the following values in the parameter file:
"numberOfVMs": total number of VMs in the cluster.  In this template,the maximum number is set to 5.  The array defined by scriptDependencies must have larger than or the same number of entries as numberOfVMs value.
"adminUsername": admin user account 
"adminPassword": admin password.  in real deployment, this should be stored in key vault and referenced here.
"scriptStorageResourceGroup": resource group name where scripts are located. This can be same resource group as the current deployment or a different one.
"scriptStorageAccount": storage account where scripts are located.
"scriptUri": uri for the script extension to get the script
"scriptCommand": command to execute the script via script extension.


This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
