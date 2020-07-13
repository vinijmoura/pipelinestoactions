### Azure Pipelines
[VSBuild](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops)

- Classic

![VS Build](images/task-VSBuild.png)

- YAML

```yaml
steps:
- task: VSBuild@1
  displayName: 'Build solution'
  inputs:
    solution: '**\*.sln'
    msbuildArgs: '/p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.artifactstagingdirectory)\\"'
    platform: '$(BuildPlatform)'
    configuration: '$(BuildConfiguration)'
```

### GitHub Actions
[VSBuild](https://github.com/marketplace/actions/setup-msbuild)
```yaml
    # Add  MSBuild to the PATH: https://github.com/microsoft/setup-msbuild
    - name: Setup MSBuild.exe
      uses: microsoft/setup-msbuild@2008f912f56e61277eefaac6d1888b750582aa16
      
    # Create the app package by building and packaging the Windows Application Packaging project
    - name: Run Msbuild
      run: msbuild $env:Solution_Name /p:platform=$env:buildPlatform /p:Configuration=$env:buildConfiguration
```
