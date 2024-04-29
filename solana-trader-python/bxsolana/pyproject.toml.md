# pyproject.toml

This `pyproject.toml` used to store metadata about the project and to configure various tools. Specifically, it is used to specify the build system, and to configure the `black` code formatter and the `pylint` static code analysis tool. Here's a breakdown of what each part does:

* `[build-system]`: This section specifies the build system for the project. `requires` is a list of packages that are required to build the project, and `build-backend` is the name of the Python module that will be used to build the project. In this case, the project uses `setuptools` to build.
* `[tool.black]`: This section configures the `black` code formatter. `line-length` specifies the maximum line length, `preview` specifies whether to use preview features, and `exclude` specifies the directories or files to exclude from formatting. In this case, the `proto` directory is excluded.
* `[tool.pylint.main]`: This section configures the `pylint` static code analysis tool. `ignore` specifies the directories or files to exclude from analysis. In this case, the `proto` directory is excluded.
