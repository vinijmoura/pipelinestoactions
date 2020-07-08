### Azure Pipelines
[Docker task](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/build/docker?view=azure-devops)

- Classic

- YAML

```yaml
steps:
- task: Docker@2
  displayName: Login to Docker Hub
  inputs:
    command: login
    containerRegistry: dockerHubServiceConnection
- task: Docker@2
  displayName: Build and Push
  inputs:
    command: buildAndPush
    repository: someUser/contoso
    tags: |
      tag1
      tag2
```

### GitHub Actions
[Build and push Docker images](https://github.com/marketplace/actions/build-and-push-docker-images)
```yaml
    uses: docker/build-push-action@v1
    with:
      username: ${{ "{{" }} secrets.DOCKER_USERNAME {{ "}} }}
      password: ${{ "{{" }} secrets.DOCKER_PASSWORD {{ "}} }}
      repository: myorg/myrepository
      tags: latest
```
