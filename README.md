# Docker
Dockerfile -> Image -> Docker Containers -> Networking -> Volume

A Dockerfile contains instructions on how to build a Docker image. Each instruction adds a layer to the image. In other words a Dockerfile provides a way to automate the setup of an environment.

To build an Image out of a Dockerfile
`docker build -t my-image-name .`

To list all images
`docker images`

A Docker image is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, libraries, environment variables, and configuration files. Docker images are used to create Docker containers, which are instances of these images running as isolated processes on the host operating system.

To start a container from a built image
`docker run -p 8080:8080 my-image-name`

The first port is the port on the host machine and the second is the port on the container.

To run multiple containers based on the same image
`docker run -d -p 8081:8080 --name spring-boot-app1 my-spring-boot-app`
`docker run -d -p 8082:8080 --name spring-boot-app2 my-spring-boot-app`

To list all containers
`docker ps`

## Contents of a Dockerfile
A Dockerfile typically includes:

-Base Image: The starting point of the Docker image, often an official image from Docker Hub.
-Working Directory: The directory in the image where the following instructions will be executed.
-Copy Commands: Commands to copy files from the host machine into the Docker image.
-Run Commands: Commands to run during the image build process (e.g., installing dependencies).
-Expose Ports: Instructions to expose ports to be accessible from outside the container.
-Entry Point or Command: Instructions to specify the command to run when the container starts.

## What a Docker Image Contains
A Docker image contains the following components:

-Base OS Layer: The underlying operating system layer (e.g., Ubuntu, Alpine).
-Application Code: The source code or binaries of the application.
-Runtime Environment: Dependencies and libraries required to run the application (e.g., JDK for Java applications, Node.js for Node.js applications).
-Configuration Files: Environment variables and configuration files needed by the application.
-Metadata: Instructions on how to set up the container environment, exposed ports, and the default command to run when the container starts.

## Docker Networking
Docker networking allows containers to communicate with each other and with the outside world.
-The default networking mode is the Bridge Network.
-Containers on the same bridge network can communicate with each other using their container names as hostnames.
-By default, containers on a bridge network are isolated from containers on other bridge networks.

To create a custom network
`docker network create my_custom_network`

To run a container on a specific network
```
docker run -d --name app1 --network my_custom_network my-image
docker run -d --name app2 --network my_custom_network my-image
```

To verify network configuration
`docker network inspect my_custom_network`

## Docker Volumes
To create a volume accessible both from the host machine and the container
`docker run -d -v /path/on/host:/path/in/container --name my-container my-image`
Or
`docker run -d --mount type=bind,source=/path/on/host,target=/path/in/container --name my-container my-image`

Example
If we have these data on the host machine
```
/host/data
  ├── train
  └── test
```

And we have the following configuration in our Dockerfile
```
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy the script into the container
COPY train.py .

# Install necessary Python packages
RUN pip install numpy pandas tensorflow

# Command to run the script
CMD ["python", "train.py"]
```

Then after building the image
`docker build -t my-python-app .`

And running the container, the script will have the data that are on host available at `/app/data`
```
import os
import pandas as pd

# List files in the data directory
data_dir = '/app/data'
print("Files in data directory:", os.listdir(data_dir))

# Assuming there are CSV files in the data directory
train_data = pd.read_csv(os.path.join(data_dir, 'train', 'train.csv'))
test_data = pd.read_csv(os.path.join(data_dir, 'test', 'test.csv'))

print("Training data head:", train_data.head())
print("Test data head:", test_data.head())
```
