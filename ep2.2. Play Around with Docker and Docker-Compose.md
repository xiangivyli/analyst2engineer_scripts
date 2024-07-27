# Commands

## Images and containers management

### Pull an image and run a container
```bash
docker run -it --container_name python:3.8
```

### List all images
```bash
docker images
```
### List all containers
```bash
docker ps -a
```
### Restart the container
```bash
docker restart <container_id_or_name>
```
### Attach to the container in the interactive mode
```bash
docker exec -it <container_id_or_name> /bin/bash
```
### Stop all running containers 
```bash
docker stop $(docker ps -q) 
```
### Remove containers
```bash
docker rm <container_id>
```
### Remove all containers
```bash
docker rm $(docker ps -aq)
```
### Remove images
```bash
docker rmi <image_id>
```
### Remove all images
```bash
docker rmi $(docker images -q)
```

## Type 1 Pull official images from Docker Hub

```bash
docker pull <image_name>
```
```bash
docker run <image_name>
```
### Dockfile Demo
```dockerfile
# Use an official Python runtime as a base image
FROM python:3.8

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```
