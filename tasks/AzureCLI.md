### Azure Pipelines
[Azure CLI](https://github.com/microsoft/azure-pipelines-tasks/blob/master/Tasks/AzureCLIV2/Readme.md)

- Classic

![Azure CLI](images/task-AzureCLI.png)

- YAML

```yaml
steps:
- task: AzureCLI@2
  displayName: 'Azure CLI '
  inputs:
    azureSubscription: '[Azure Subscription]'
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
     az account show
     az storage -h
```
### GitHub Actions
[Azure CLI](https://github.com/marketplace/actions/azure-cli-action)
```yaml
    - name: Azure Login
      uses: Azure/login@v1.1
      with:
        creds: {% raw  %}${{secrets.AZURE_CREDENTIALS}}{% endraw %}

    - name: Azure CLI script
      uses: azure/CLI@v1
      with:
        azcliversion: 2.0.72
        inlineScript: |
          az account show
          az storage -h 
```
