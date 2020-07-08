### Azure Pipelines
[Docker task](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/build/docker?view=azure-devops)

- Classic

![Docker (build)](images/task-Docker-build.png)
![Docker (push)](images/task-Docker-push.png)

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
      username: {% raw  %}${{secrets.DOCKER_USERNAME}}{% endraw %}
      password: {% raw  %}${{secrets.DOCKER_PASSWORD}}{% endraw %}
      repository: myorg/myrepository
      tags: latest
```
