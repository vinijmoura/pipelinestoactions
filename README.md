# Azure Pipelines to GitHub Actions
Use this guidance to rewrite Azure Pipelines (Build and Release Tasks) on GitHub Actions.

## Azure SQL Deploy

#### [Classic](#tab/classic/)
#### [YAML](#tab/yaml/)
```yaml
```
#### [GitHub Actions](#tab/gha/)
```yaml
  - name: Azure SQL Deploy
    uses: Azure/sql-action@v1
    with:
      server-name: ${{ secrets.SQL_SERVERNAME }}
      connection-string: ${{ secrets.AZURE_SQL_CONNECTION_STRING }}
      dacpac-package: ./[Project Name]/bin/${{ env.buildConfiguration }}/GHA-SSDT.dacpac
```
