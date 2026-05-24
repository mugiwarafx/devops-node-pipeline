# DevOps with Docker 2026 - Exercise 3.1

This repository contains my solution for Exercise 3.1: Your pipeline.

The project is a simple Node.js/Express application with a deployment pipeline.

## Pipeline

On every push to the `master` branch, GitHub Actions:

1. Checks out the repository.
2. Sets up Docker Buildx.
3. Logs in to Docker Hub using repository secrets.
4. Builds the Docker image.
5. Pushes the image to Docker Hub.

The pushed image is:

```txt
superjordi/devops-node-pipeline:latest
```

## Required Secrets

The GitHub repository needs these Actions secrets:

```txt
DOCKER_USERNAME
DOCKER_PASSWORD
```

`DOCKER_PASSWORD` is a Docker Hub access token.

## Running Locally

After the GitHub Actions workflow has pushed the image, start the application with:

```bash
docker compose pull
docker compose up -d
```

Check the application:

```bash
curl http://localhost:3000
```

Watchtower is included in `docker-compose.yaml` and checks for updated images every 60 seconds.
