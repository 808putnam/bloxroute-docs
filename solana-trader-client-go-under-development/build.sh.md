# build.sh

The `build.sh` file is a shell script that builds a Docker image for the Solana Trader Client Go application.

Here's a brief overview of what each line does:

1. `#!/usr/bin/env bash`: This is the shebang line that tells the system this script should be executed using bash.
2. `IMAGE=bloxroute/solana-trader-client-go:${1:-latest}`: This line sets the `IMAGE` variable to the Docker image name. It uses the first command-line argument (`$1`) as the tag for the Docker image. If no argument is provided, it defaults to "latest".
3. `docker build . -f Dockerfile --rm=true -t $IMAGE --platform linux/amd64`: This line runs the `docker build` command to build the Docker image. It specifies the current directory (`.`) as the build context, uses the `Dockerfile` in the current directory, removes intermediate containers after a successful build (`--rm=true`), tags the image with the name stored in the `IMAGE` variable (`-t $IMAGE`), and sets the platform for the build to `linux/amd64`.
