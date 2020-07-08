### Azure Pipelines
[MSBuild](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/build/msbuild?view=azure-devops)

- Classic

![MS Build](images/task-MSBuild.png)

- YAML

```yaml
steps:
- task: MSBuild@1
  displayName: 'Build solution **/*.sln'
  inputs:
    platform: '$(BuildPlatform)'
    configuration: '$(Buildconfiguration)'
    msbuildArguments: '/p:OutputPath=$(Build.ArtifactStagingDirectory)'
```

### GitHub Actions
[MSBuild](https://github.com/marketplace/actions/setup-msbuild)
```yaml
    # Add  MSBuild to the PATH: https://github.com/microsoft/setup-msbuild
    - name: Setup MSBuild.exe
      uses: microsoft/setup-msbuild@2008f912f56e61277eefaac6d1888b750582aa16
      
    # Create the app package by building and packaging the Windows Application Packaging project
    - name: Run Msbuild
      run: msbuild $env:Solution_Name /p:platform=$env:buildPlatform /p:Configuration=$env:buildConfiguration
```
