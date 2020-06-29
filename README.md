# Azure Pipelines to GitHub Actions
Use this guidance to rewrite Azure Pipelines (Build and Release Tasks) on GitHub Actions.

## Azure SQL DacpacTask (Pipelines) x Azure SQL Deploy (GitHub Actions)

### Azure Pipelines
- Classic
  - [Azure SQL Deploy](https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/SqlAzureDacpacDeploymentV1)
- YAML
  ```yaml
  steps:
  - task: SqlAzureDacpacDeployment@1
    displayName: 'Azure SQL DacpacTask'
    inputs:
      azureSubscription: '[Subscription Name]'
      ServerName: '$(SQLServer)'
      DatabaseName: '$(SQLDatabase)'
      SqlUsername: '$(Login)'
      SqlPassword: '$(Pwd)'
      DacpacFile: '$(System.DefaultWorkingDirectory)/_[Project Name]/drop/[Project Name]/bin/Release/[Project Name].dacpac'
  ```
### GitHub Actions
- [Azure SQL Deploy](https://github.com/marketplace/actions/azure-sql-deploy)
```yaml
  - name: Azure SQL Deploy
    uses: Azure/sql-action@v1
    with:
      server-name: ${{ secrets.SQL_SERVERNAME }}
      connection-string: ${{ secrets.AZURE_SQL_CONNECTION_STRING }}
      dacpac-package: ./[Project Name]/bin/${{ env.buildConfiguration }}/GHA-SSDT.dacpac
```

## MSBuild
#### [Classic](#tab/classic/)
#### [YAML](#tab/yaml/)
#### [GitHub Actions](#tab/gha/)

# References
## GitHub Actions
- [GitHub Actions](https://github.com/features/actions)
## GitHub Marketplace
- [GitHub Markeplace](https://github.com/marketplace?type=actions)
