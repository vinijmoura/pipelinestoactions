<!--DOCUSAURUS_CODE_TABS-->

<!--### Azure Pipelines-->
[Azure Web App](https://github.com/Microsoft/azure-pipelines-tasks/blob/master/Tasks/AzureWebAppV1/README.md)

- Classic

![Azure Web App](images/task-AzureWebApp.png)

- YAML

```yaml
steps:
- task: AzureWebApp@1
  displayName: 'Azure Web App'
  inputs:
    azureSubscription: '[Subscription]'
    appType: webApp
    appName: [App Name]
    package: '$(System.DefaultWorkingDirectory)\**\*.zip'
```
<!--### GitHub Actions-->
[Azure Web App](https://github.com/marketplace/actions/azure-webapp)
```yaml
    - name: Azure Login
      uses: Azure/login@v1.1
      with:
        creds: {% raw  %}${{secrets.AZURE_CREDENTIALS}}{% endraw %}

    - name: Deploy to Azure Web App
      uses: azure/webapps-deploy@v1
      with:
        app-name: '[App Name]'
        package: {% raw  %}${{env.DOTNET_ROOT}}{% endraw %}/myapp 
```
<!--END_DOCUSAURUS_CODE_TABS-->
