# build container
FROM golang:1.27-bookworm

WORKDIR /src

COPY go.* .
COPY main.go .

RUN CBO_ENABLED=0 go build -o app .

# run container
FROM debian:bookworm

WORKDIR /app

COPY --from=builder /src/app .

ENV PORT="3000" INSTANCE_NAME="dov-bear" INSTANCE_HASH=""

EXPOSE ${PORT}

SHELL [ "/bin/sh", "-c"]
ENTRYPOINT ./app