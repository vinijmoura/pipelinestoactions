# Azure Pipelines to GitHub Actions

Use this guidance to rewrite Azure Pipelines (Build and Release Tasks) on GitHub Actions.


## Table of contents
---
<!--ts-->
   * [`MSBuild`](#MSBuild)
   * [`DotNetCore`](#DotNetCore)
   * [`Azure SQL`](#azure-sql)
   * [`Docker`](#docker)
<!--te-->

---


## MSBuild
{% include_relative /tasks/MSBuild.md %}

## DotNetCore
{% include_relative /tasks/DotNetCoreCLI.md %}

## Azure SQL
{% include_relative /tasks/SQLAzure.md %}

## Docker
{% include_relative /tasks/Docker.md %}

---


## References

- [GitHub Actions](https://github.com/features/actions)
- [GitHub Markeplace](https://github.com/marketplace?type=actions)

## Contribute

Contributions to **Pipelines to GitHub Actions** are welcome. Please fork this repo.

- Include on `ReadMe.md` a respective task/action that you want to document (`Table of contents` section).
```yaml
{% include_relative /tasks/[NEW TASK].md %}
```

![Table of contents](images/table-of-contents.png)

- Create new markdown file under `Tasks` folder and describe Azure Pipeline Tasks and respetive GitHub Actions. Use as an example [DotNetCore](/tasks/DotNetCoreCLI.md).

![Include Tasks](images/include-tasks.png)