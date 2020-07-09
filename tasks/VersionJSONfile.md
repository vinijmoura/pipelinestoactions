### Azure Pipelines
[Manifest Versioning Build Tasks](https://marketplace.visualstudio.com/items?itemName=richardfennellBM.BM-VSTS-Versioning-Task)

- Classic

![Version JSON File](images/task-VersionJSONFile.png)

- YAML

```yaml
steps:
- task: VersionJSONFile@2
    inputs:
      Path: '$(Build.SourcesDirectory)'
      recursion: True
      VersionNumber: '$(Build.BuildNumber)'
      useBuildNumberDirectly: False
      VersionRegex: '\d+\.\d+\.\d+\.\d+'
      versionForJSONFileFormat: '{1}.{2}.{3}'
      FilenamePattern: 'package.json'
      OutputVersion: 'OutputedVersion'
  ```
### GitHub Actions
[Apply Version to JSON file](https://github.com/marketplace/actions/apply-version-to-json-file)
```yaml
- name: Apply Version to JSON file
  uses: rfennell/JSONFileVersioner@v1
  with:
    path: 'testdata'
    field: 'version'
    VersionNumber: '1.2.3'
    filenamepattern: '.json' 
    recursion: 'true'
```
