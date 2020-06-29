# Azure Pipelines to GitHub Actions
Use this guidance to rewrite Azure Pipelines (Build and Release Tasks) on GitHub Actions.

Table of contents
=================

<!--ts-->
   * [MSBuild](#MSBuild)
   * [Azure SQL DacpacTask (Pipelines) x Azure SQL Deploy (GitHub Actions)](#Azure-SQL-DacpacTask-(Pipelines)-x-Azure-SQL-Deploy-(GitHub-Actions))

    
<!--te-->

## MSBuild
#### [Classic](#tab/classic/)
#### [YAML](#tab/yaml/)
#### [GitHub Actions](#tab/gha/)
```yaml
    # Add  MSBuild to the PATH: https://github.com/microsoft/setup-msbuild
    - name: Setup MSBuild.exe
      uses: microsoft/setup-msbuild@2008f912f56e61277eefaac6d1888b750582aa16
      
    # Create the app package by building and packaging the Windows Application Packaging project
    - name: Run Msbuild
      run: msbuild $env:Solution_Name /p:platform=$env:buildPlatform /p:Configuration=$env:buildConfiguration
```

## Azure SQL DacpacTask (Pipelines) x Azure SQL Deploy (GitHub Actions)

### Azure Pipelines
[Azure SQL DacpacTask](https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/SqlAzureDacpacDeploymentV1)
- Classic

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

# References
## GitHub Actions
- [GitHub Actions](https://github.com/features/actions)
## GitHub Marketplace
- [GitHub Markeplace](https://github.com/marketplace?type=actions)
