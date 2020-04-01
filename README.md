# WVD Deploy | Host PS Script

The framework for this script were sourced from [Azure/RDS-Templates/wvd-sh/Create and provision WVD host pool/](https://github.com/Azure/RDS-Templates/tree/master/wvd-sh/Create%20and%20provision%20WVD%20host%20pool)

Script was updated to be one master standalone script, which downloads nessecary tools and configures a Azure VM as a [WVD Host](https://docs.microsoft.com/en-us/azure/virtual-desktop/overview) and joins it to the specified WVD Host Pool.

### BETA WARNING
This Script is still under testing and has not been tested in all scenarios 
Test | Host OS | Status
--- | --- | ---
Running Locally On Domain Joined Host | Win10 1909 Multi-Session | Testing in progress
ARM Template Custom Script Extension | Win10 1909 Multi-Session  | Testing in progress
Running Locally On Domain Joined Host | WinSrv 2016 | Planned Testing
Running Locally On Domain Joined Host | WinSrv 2019 | Planned Testing

### BETA WARNING

## Script Parameters

Parameter | Required | Description
--- | --- | ---
RDBrokerURL | Yes | https://rdbroker.wvd.microsoft.com
definedTenantGroupName | Yes | WVD Tenant Group Name
TenantName | Yes | Name of the WV
HostPoolName | Yes | Name of the WVD Host Pool 
Description | Yes | Host Pool Description 
FriendlyName  | Yes | Host Pool Friendly Name
Hours |  | 48
TenantAdminUPN | | WVD Tenant Admin UPN
TenantAdminPassword | | 
localAdminUserName | | 
localAdminPassword | | 
rdshIs1809OrLater | | $true
isServicePrincipal | | $true if using Service Principal for credentials 
AadTenantId | | AAD Tenant ID being used for WVD 
