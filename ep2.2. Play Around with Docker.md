# Commands

## Type 1 Pull official images from Docker Hub

```bash
docker pull <image_name>
```
```bash
docker run -it --name <container_name> <image_name>:tag /bin/bash
```

## Images and containers management

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

## Type 2 Customise an image from Dockfile

### requirements.txt demo
```txt
pandas==1.5.3
```

### Dockerfile Demo
```dockerfile
# Use an official Python runtime as a base image
FROM python:3.8

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Define the command that runs when container starts
CMD ["bash"]
```

### Build the image
```bash
docker build -t my_python_app:1.0 .
```

### app.py demo
```python
import pandas as pd

df = pd.DataFrame({
    'number': [1, 2, 3, 4, 5],
    'career': ["biology", "pathology", "database_manager", "business_analytics", "data_engineer"]
})

print("ivy's career:")
print(df)
```


