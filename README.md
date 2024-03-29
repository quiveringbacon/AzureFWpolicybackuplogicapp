# Azure Firewall policy backup and restore logic apps
backs up and restores Azure firewall policies using logic apps and storage accounts

This ARM template creates a storage account and 2 logic apps. The first logic app runs every 3 days and exports an ARM template for each firewall policy rule collection group  and saves them to the storage account. The second logic app is disabled by default and can be enabled when needed and uses an HTTP trigger looking for the resource group to restore the policy to in the body (example: {"rg":"rg111"}). The restore app restores the templates from the storage account with a 1 minute delay between each rule collection group deployment.
Both logic apps use managed identities that have contributor access to the resource group they are deployed in and storage blob data contributor access to the storage account.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fquiveringbacon%2FAzureFWpolicybackuplogicapp%2Fmain%2Ftemplate-newapp1.json)
