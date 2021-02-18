### Azure Pipelines
[Publish Artifact](https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/PublishBuildArtifactsV1)

- Classic

![Publish Artifacts](images/publish-artifacts.png)

- YAML

```yaml
steps:
- task: CopyFiles@2
  inputs:
    SourceFolder: '$(Build.SourcesDirectory)'
    Contents: '*.yml'
    TargetFolder: '$(Build.ArtifactStagingDirectory)'
- task: PublishBuildArtifacts@1
    inputs:
    PathtoPublish: '$(Build.ArtifactStagingDirectory)'
    ArtifactName: 'drop'
    publishLocation: 'Container'
  ```
### GitHub Actions
[Upload a Build Artifact](https://github.com/marketplace/actions/upload-a-build-artifact)
```yaml
- name: Copy JMeter Files
  shell: pwsh
  run: |
    Copy-Item -Path ./deploy.yml -Destination ${{ env.DROP_LOCATION }} -Force
- name: Publish Artifacts
uses: actions/upload-artifact@v1.0.0
with:
    name: drop
    path: ${{ env.DROP_LOCATION }}
```
