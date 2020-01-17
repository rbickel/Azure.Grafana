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

**Deployment**
```
New-AzResourceGroupDeployment -ResourceGroupName "Grafana" -TemplateFile "azuredeploy.json" -TemplateParameterFile "azuredeploy.parameters.json"
```

