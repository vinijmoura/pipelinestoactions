### Azure Pipelines
[IIS web app deploy](https://github.com/microsoft/azure-pipelines-tasks/blob/master/Tasks/IISWebAppDeploymentOnMachineGroupV0/README.md)

- Classic

![MS Build](images/task-MSBuild-DeployIIS-1.png)
![MS Deploy](images/task-MSBuild-DeployIIS-2.png)

- YAML

```yaml
#MSBuild
steps:
- task: VSBuild@1
  displayName: 'Build solution'
  inputs:
    solution: '$(Parameters.solution)'
    msbuildArgs: '/p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.artifactstagingdirectory)\\"'
    platform: '$(BuildPlatform)'
    configuration: '$(BuildConfiguration)'

#MSDeploy
steps:
- task: IISWebAppDeploymentOnMachineGroup@0
  displayName: 'Deploy IIS Website/App: '
  inputs:
    WebSiteName: $(WebSiteName)

```

### GitHub Actions
[Setup Nuget.exe](https://github.com/marketplace/actions/setup-nuget-exe)
[Setup MSBuild.exe](https://github.com/marketplace/actions/setup-msbuild-exe)

```yaml
    env:
      Solution_Name: 'mySoltion.sln'                      
      buildPlatform: 'Any CPU'
      buildConfiguration: 'Release'
      WebSiteName: 'mySite'
      zipName: 'mySolution.zip'
    
    steps:
      
    - name: Checkout
      uses: actions/checkout@v2      
      
    - name: Setup Nuget.exe
      uses: warrenbuckley/Setup-Nuget@v1
      
    - name: Restore Packages
      run: nuget restore $env:Solution_Name
  
    - name: Setup MSbuild.exe
      uses: warrenbuckley/Setup-MSBuild@v1
      
    - name: Build using MSBuild
      run: msbuild $env:Solution_Name /p:platform=$env:buildPlatform /p:Configuration=$env:buildConfiguration /p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation='C:\myapp'
          
    - name: Run MSDeploy.exe
      run: msdeploy -verb:sync -source:package=C:\myapp\{% raw  %}${{ env.zipName }}{% endraw %}.zip -dest:auto -setParam:name=`'IIS Web Application Name`',value=$env:WebSiteName -enableRule:DoNotDeleteRule
```
