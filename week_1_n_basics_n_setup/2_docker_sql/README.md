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

### `docker run hello-world` Command

```bash
docker run hello-world
```

### What it Does
The docker run hello-world command is a simple command used to verify that Docker is installed and working correctly on your system. When you run this command, Docker will:

- Check if the hello-world image is available locally on your machine.

- If the image is not found, Docker will automatically download (pull) the hello-world image from Docker Hub.

- Once the image is available, Docker will run it inside a container, which will print a confirmation message to the terminal, letting you know that Docker is functioning properly.

### Expected Output
When you successfully run `docker run hello-world`, you should see the following message:

```bash
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

### `docker run -it ubuntu bash` Command

```bash
docker run -it ubuntu bash
```

### What it Does
The docker run -it ubuntu bash command starts an interactive Ubuntu container and opens a bash shell inside it.

-it: Combines -i (interactive) and -t (terminal) to allow you to interact with the container.

ubuntu: Uses the official Ubuntu image to create the container.

bash: Starts the bash shell inside the container.

### Expected Output
After running the command, you should see:

```bash
root@<container_id>:~#
```

This indicates you're inside the container, and you can run bash commands. To exit, just type exit.

### `docker run -it python:3.9` Command

```bash
docker run -it python:3.9
```
### What it Does
The docker run -it python:3.9 command creates a new container from the official Python 3.9 Docker image and opens an interactive terminal session.

-it: Combines two options:

-i (interactive): Keeps the standard input open, allowing interaction with the container.

-t (terminal): Allocates a terminal to the container for a more readable, interactive interface.

python:3.9: Specifies the Docker image to use for creating the container. Here, python is the official Docker image for Python, and 3.9 is the specific version tag, meaning it will use Python version 3.9.

This command is often used when you want to run a Python 3.9 environment inside a container, allowing you to execute Python commands interactively.

### `docker run -it --entrypoint=bash python:3.9` Command

```bash
docker run -it --entrypoint=bash python:3.9
```

### What it Does
This command runs a container from the Python 3.9 Docker image, but instead of launching the Python interpreter, it opens a bash shell.

## Why Use a Dockerfile?

A **Dockerfile** is a script that contains a list of instructions for building a Docker image.

#### ✅ Benefits:
- **Automation**: Automatically sets up your environment and installs dependencies.
- **Reproducibility**: Ensures consistent builds across all environments.
- **Version Control**: You can track and update how your image is built.
- **Customization**: Tailor the environment exactly to your application's needs.

Instead of building images manually, you define everything in a Dockerfile once—and reuse it anywhere.

#### 🧱 Common Dockerfile Instructions

- `FROM`: Specifies the base image (e.g., `python:3.9`).
- `COPY`: Copies files from your machine into the image.
- `RUN`: Runs commands inside the image (e.g., install packages).
- `CMD`: Sets the default command to run when the container starts.
- `ENTRYPOINT`: Sets the main executable for the container, which always runs.
- `WORKDIR`: Sets the working directory inside the container.
- `EXPOSE`: Documents which ports the container uses.

### 🏃‍♀️ How to Run a Dockerfile

#### 1. Build the Docker Image

Navigate to the directory where your `Dockerfile` is located and run:

```bash
docker build -t my-image-name .
```
- -t my-image-name: Tags (names) your image so you can refer to it later.

- .: Tells Docker to use the current directory as the build context (where the Dockerfile and other files are).

#### 2. Run the Container
After building the image, start a container using:

docker run my-image-name

## 🐘 Running PostgreSQL in a Docker Container
After setting up a Python virtual environment and installing pgcli (a command-line interface for PostgreSQL), I ran a PostgreSQL container using Docker with the following command:

```bash
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data \
  -p 5431:5432 \
  postgres:13
```

- -it: Runs the container in interactive mode with a terminal.

- docker run: Creates and starts the container from the specified image.

- postgres:13: The PostgreSQL image to run. Docker pulls it if it's not already on the system.

- POSTGRES_USER: The name of the PostgreSQL user I want to create.

- POSTGRES_PASSWORD: The password for the user.

- POSTGRES_DB: The name of the database to create.

- -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data: Mounts a local directory into the container to persist data. This ensures my data isn’t lost when the container stops or is removed.

- -p 5431:5432: Maps port 5432 in the container to port 5431 on my machine. I used 5431 because 5432 was already in use.

Now you can connect to this database. Open a new terminal and install client **pgcli** and connect to this database.

- Install:
```bash
pip install pgcli
```

- Connect to postgresql database:
```bash
pgcli -U root -d ny_taxi -h localhost
```



