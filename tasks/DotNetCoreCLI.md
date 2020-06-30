### Azure Pipelines
[.Net Core CLI](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/build/dotnet-core-cli?view=azure-devops)

- Classic

- YAML
```yaml
steps:
- task: DotNetCoreCLI@2
  displayName: Restoring .Net packages
  inputs:
    command: 'restore'
- task: DotNetCoreCLI@2
  displayName: Building code
  inputs:
    command: 'build'
    projects: '**/*.csproj'
    arguments: '--configuration $(buildConfiguration)'
- task: DotNetCoreCLI@2
  displayName: Running unit tests
  inputs:
    command: test
    projects: '**/*Tests/*.csproj'
    arguments: '--configuration $(buildConfiguration)'
```

### GitHub Actions
[.Net Core SDK](https://github.com/marketplace/actions/setup-net-core-sdk)
```yaml
    # Install .Net Core SDK: https://github.com/actions/setup-dotnet
    - name: Setup .NET Core
      uses: actions/setup-dotnet@v1
      with:
        dotnet-version: 3.1.101
    - name: Install dependencies
      run: dotnet restore
    - name: Build
      run: dotnet build --configuration Release --no-restore
    - name: Test
      run: dotnet test --no-restore --verbosity normal
```