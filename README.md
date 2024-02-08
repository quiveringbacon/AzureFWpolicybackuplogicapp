# Azure Firewall policy backup and restore logic apps
backs up and restores Azure firewall policies using logic apps and storage accounts

This ARM template creates a storage account and 2 logic apps. The first logic app runs every 3 days and exports an ARM template for each firewall policy rule collection group  and saves them to the storage account. The second logic app is disabled by default and can be enabled when needed and uses and HTTP trigger looking for the resource group to restore the policy to in the body (example: {"rg":"rg111"}). The restore app restores the templates from the storage account with a 1 minute delay between each rule collection group deployment.
Both logic apps use managed identities that have contributor access to the resource group they are deployed in and storage blob data contributor access to the storage account.
