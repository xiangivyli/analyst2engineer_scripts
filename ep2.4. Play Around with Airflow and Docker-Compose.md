# Part A Install Astro and Play Around with Containers

## Step 1. Install Astro CLI
Link: https://www.astronomer.io/docs/astro/cli/install-cli?tab=linux#install-the-astro-cli

```bash
curl -sSL install.astronomer.io | sudo bash -s -- v1.28.1
```

## Step 2. Astro Dev 
```bash
astro dev init
```
```bash
astro dev start
```

## Step 3. Play Around with Containers
```bash
docker exec -it <webserver_container_name> /bin/bash
```
Or 
```bash
astro dev bash <webserver_container_name>
```

# Part B Add Streamlit Container

### docker-compose.override.yml
```yml
services:
  streamlit_app:
    image: python:3.8-slim
    command: >
      bash -c "pip install -r /app/include/streamlit_requirements.txt && \
      stream run /app/include/streamlit_app.py
      "
    ports:
      - "8501:8501"
    volumes:
      - ./include:/app/include
```

### Astro rebuilds the containers



# Part C Divide the data flow into tasks




