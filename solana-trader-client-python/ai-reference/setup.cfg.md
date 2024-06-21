# setup.cfg

The `setup.cfg` file is a configuration file for setuptools, a library in Python used to distribute Python packages. This `setup.cfg` file is used to specify the metadata and options for building, installing, and distributing the `bxsolana-trader` Python package.

Here's a breakdown of what each part does:

* `[metadata]`: This section contains metadata about the project, such as the name, version, description, author, and more. The `long_description` field is set to the contents of the `README.md` and `LICENSE` files.
* `[options]`: This section contains options for building, installing, and distributing the package. The `packages` field is set to `find:`, which means setuptools will automatically discover all packages in the project. The `install_requires` field lists the dependencies that will be installed by pip when the project is installed.

