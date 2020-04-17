# WVD Deploy | Setup-WVDHost.ps1 Script

This powershell script performs the operations nessecary to prepare and join a domain joined Azure VM to a [WVD Host Pool](https://docs.microsoft.com/en-us/azure/virtual-desktop/overview). It functions as a standalone script and downloads all of the nessecary tools and applications from public endpoints to ensure that the most current version is being used.

The following items will be installed on the server-

* Microsoft.RDInfra.RDAgentBootLoader.Installer-x64.msi
* Microsoft.RDInfra.RDAgent.Installer-x64.msi
* FSLogixAppsSetup.exe (no GPOs or settings configured) 

The framework for this script were sourced from [Azure/RDS-Templates/wvd-sh/Create and provision WVD host pool/](https://github.com/Azure/RDS-Templates/tree/master/wvd-sh/Create%20and%20provision%20WVD%20host%20pool)


 ` Setup-WVDHost.ps1 -RDBrokerURL "https://rdbroker.wvd.microsoft.com" -definedTenantGroupName "Default Tenant Group" -TenantName <myTenantName> -HostPoolName <myHostPoolName> -Hours <int for RdsRegistrationInfo expiration> -TenantAdminUPN <TenantAdminUPN or SPN ID> -TenantAdminPassword <Super Secret Password> -isServicePrincipal <bool> -AadTenantId <AAD Tenant GUID> `


## Script Parameters

Parameter | Required | Description
--- | --- | ---
RDBrokerURL | Yes | https://rdbroker.wvd.microsoft.com
definedTenantGroupName | Yes | Default Tenant Group
TenantName | Yes | Name of existing WVD Tenant
HostPoolName | Yes | Name of the WVD Host Pool (if pool does not exist it will be created)
Description | Conditional | Host Pool Description if creating new Host Pool  
FriendlyName  | Conditional | Host Pool Friendly Name if creating new Host Pool
Hours | Yes | Number of hours new RdsRegistrationInfo will be valid for, if valid RdsRegistrationInfo exists for Tenant and Host Pool it will be used 
TenantAdminUPN | Yes | WVD Tenant Admin UPN or Service Principal App ID
TenantAdminPassword | Yes | WVD Tenant Admin or Service Principal Secret
isServicePrincipal | Bool| $true if using Service Principal for WVD Tenant credentials 
AadTenantId | Yes | AAD Tenant ID GUID being used for WVD 
