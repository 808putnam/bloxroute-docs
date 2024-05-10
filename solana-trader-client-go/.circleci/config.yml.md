# config.yml

The `config.yml` file is a configuration file for CircleCI, a continuous integration and delivery platform. It defines the steps that CircleCI will take to build, test, and deploy the application.

Here's a brief overview of what each section does:

1. `version`: Specifies the CircleCI configuration version. The current version is 2.1.
2. `executors`: Defines an executor named `bxgo` that uses a Docker image with Go 1.18 installed. It sets several environment variables and specifies the working directory.
3. `jobs`: Defines several jobs that CircleCI can run:
   * `init`: Sets up the workspace, checks out the code, installs necessary packages, downloads dependencies, and saves the workspace for later jobs.
   * `unit`: Runs unit tests.
   * `integration-testnet`: Runs integration tests on the testnet environment.
   * `integration-mainnet`: Runs integration tests on the mainnet environment.
4. `workflows`: Defines two workflows:
   * `test-branch`: Runs the `init` and `unit` jobs when the pipeline is not triggered by a schedule.
   * `nightly`: Runs the `init`, `unit`, `integration-testnet`, and `integration-mainnet` jobs when the pipeline is triggered by a schedule.

