# Azure.Grafana

## About

Azure ARM template project to deploy a Grafana container on Azure AppServices, a MySQL Database, and secured using Firewall rules, Frontdoor and Web Application Firewall.

[![Build Status](https://dev.azure.com/rabickel/Azure.Grafana/_apis/build/status/rbickel.Azure.Grafana?branchName=master)](https://dev.azure.com/rabickel/Azure.Grafana/_build/latest?definitionId=31&branchName=master)


### Architecture

![Architecture diagram](/Architecture.png)

*Contribution are greatly welcomed* :)

[![Deploy to Azure](https://azurecomcdn.azureedge.net/mediahandler/acomblog/media/Default/blog/deploybutton.png)](https://azuredeploy.net/)

## Backlog

* [x] Implement template with Grafana container and MySQL

* [x] Secure MySQL connection with SSL and Firewall rules

* [x] Deploy Frontdoor with WAF prevention policies tailored for Grafana

* [x] Secure AppService to accept traffic only from Frontdoor

* [x] Add Azure AD Authentication

* [ ] Secure AppService to accept traffic only from Frontdoor specific instance

* [ ] Add Diagnostic logs to Frontdoor, AppServices and MySQL



## Getting strated

**Prerequisites**

1. Create the AppRegistration for AAD authentication
```Powershell
//replace the variables with your current values
$FrontdoorRootUrl = "https://my-grafana-frontdoor.azurefd.net"
$MyAppRegistrationSecret = "1234567890@Grafana!"
$OAuthReplyUrl = "$FrontdoorRootUrl/login/generic_oauth"

az ad app create --display-name $FrontdoorRootUrl --identifier-uris $FrontdoorRootUrl --required-resource-accesses ./manifest.json --reply-urls $OAuthReplyUrl --password $MyAppRegistrationSecret
```

2. Edit the parameter file

**Deploy the solution**
```
New-AzResourceGroupDeployment -ResourceGroupName "Grafana" -TemplateFile "azuredeploy.json" -TemplateParameterFile "azuredeploy.parameters.json"
```


## Contributions

This project welcomes contributions and suggestions.  Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit https://cla.microsoft.com.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

