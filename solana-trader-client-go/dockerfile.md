# Dockerfile

The `Dockerfile` is used to build a Docker image for the Solana Trader Client Go application. Note that it sets up running the application as a non-root user.

Here's a brief overview of what each section does:

1. `FROM golang:1.18 as builder`: This line sets the base image for the build stage to `golang:1.18`. The `as builder` part names this build stage "builder".
2. `RUN mkdir -p /app/solana-trader-client-go`: This line creates a directory for the application.
3. `WORKDIR /app/solana-trader-client-go`: This line sets the working directory for the following instructions.
4. `COPY . .`: This line copies the current directory on the host to the current directory in the image.
5. `RUN go mod download`: This line downloads the dependencies defined in the `go.mod` file.
6. `RUN rm -rf bin` and `RUN go build -o bin/ ./benchmark/traderapi`: These lines remove the existing `bin` directory and compile the application, placing the output binary in the `bin` directory.
7. `FROM golang:1.18`: This line starts a new build stage with `golang:1.18` as the base image.
8. `RUN apt-get update` and `RUN apt-get install -y net-tools`: These lines update the package lists and install the `net-tools` package.
9. `RUN useradd -ms /bin/bash solana-trader-client-go`: This line creates a new user for running the application.
10. `RUN mkdir -p /app/solana-trader-client-go` and `RUN chown -R solana-trader-client-go:solana-trader-client-go /app/solana-trader-client-go`: These lines create the application directory and change its ownership to the new user.
11. `COPY --from=builder /app/solana-trader-client-go/bin /app/solana-trader-client-go/bin`: This line copies the `bin` directory from the "builder" stage to the current stage.
12. `ENTRYPOINT ["/app/solana-trader-client-go/bin/traderapi"]`: This line sets the default command to run when the container starts. It runs the application binary.

