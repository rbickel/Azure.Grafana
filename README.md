# Azure.Grafana

Azure ARM template project to deploy a Grafana container on Azure AppServices, a MySQL Database, and secured using Firewall rules, Frontdoor and Web Application Firewall.

*Contribution are greatly welcomed* :)

[![Deploy to Azure](https://azurecomcdn.azureedge.net/mediahandler/acomblog/media/Default/blog/deploybutton.png)](https://azuredeploy.net/)

**Backlog**:

[**X**] Implement template with Grafana container and MySQL

[**X**] Secure MySQL connection with SSL and Firewall rules

[**X**] Deploy Frontdoor with WAF prevention policies tailored for Grafana

[**X**] Secure AppService to accept traffic only from Frontdoor

[**X**] Add Azure AD Authentication

[ ] Secure AppService to accept traffic only from Frontdoor specific instance

[ ] Add Diagnostic logs to Frontdoor, AppServices and MySQL


**Architecture**

![Architecture diagram](/Architecture.png)

**Deployment**

Prerequisites
1. Create the AppRegistration for AAD authentication
```Powershell
//replace the variables with your current values
$FrontdoorRootUrl = "https://my-grafana-frontdoor.azurefd.net"
$MyAppRegistrationSecret = "1234567890@Grafana!"
$OAuthReplyUrl = "$FrontdoorRootUrl/login/generic_oauth"

az ad app create --display-name $FrontdoorRootUrl --identifier-uris $FrontdoorRootUrl --required-resource-accesses ./manifest.json --reply-urls $OAuthReplyUrl --password $MyAppRegistrationSecret
```

Deploy the solution
```
New-AzResourceGroupDeployment -ResourceGroupName "Grafana" -TemplateFile "azuredeploy.json" -TemplateParameterFile "azuredeploy.parameters.json"
```