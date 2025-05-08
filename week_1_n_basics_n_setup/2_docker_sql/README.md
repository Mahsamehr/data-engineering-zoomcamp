# Docker: Overview & Usage

## What is Docker?
Docker is a platform that allows developers to package applications and all of their dependencies into standardized units called **containers**. These containers can run consistently across different environments, whether on a developer's machine, in testing, or in production.

## Why Use Docker?
- **Consistency**: Ensures the application runs the same in any environment by packaging all dependencies.
- **Portability**: Containers can run on any system with Docker installed.
- **Isolation**: Each container is isolated, allowing multiple applications to run without conflict.
- **Efficiency**: Simplifies deployment and scales easily across systems.

This makes Docker an essential tool for modern development, enhancing both productivity and reliability.

## What is a Docker Image?

A **Docker image** is a **read-only template** that contains everything needed to run an application — including the code, runtime, libraries, environment variables, and configuration files.

Think of it as a **blueprint** for creating Docker containers.

### 🧱 Key Points:
- **Immutable**: Once built, the image does not change.
- **Built from a Dockerfile**.
- Used to **create containers** (`docker run <image>`).
- Can be stored locally or in remote repositories like **Docker Hub**.


## `docker run hello-world` Command

The `docker run hello-world` command is used to test whether Docker is functioning properly by running a simple test image.

### Command

```bash
docker run hello-world