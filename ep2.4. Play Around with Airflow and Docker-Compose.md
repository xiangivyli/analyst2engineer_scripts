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

```bash
docker logs <container_name>
```

# Part B Add Streamlit Container

### 1. Rename the `requirements.txt` to `streamlit_requirements.txt` and put it in the include


### 2. Covert the Dockerfile for streamlit into service in the `docker-compose.override.yml`
```yml
services:
  streamlit_app:
    image: python:3.8-slim
    command: >
      bash -c "python3 -m venv .venv && \
      source .venv/bin/activate && \
      pip install --upgrade pip && \
      pip install -r /include/streamlit_requirements.txt && \
      streamlit run /include/streamlit_app.py"
    ports:
      - "8501:8501"
    volumes:
      - ./include:/include
```
### 3. Adjust the data path
`data_file_path = "/include/data.csv"` in the `streamlit_app.py`

### Astro rebuilds the containers
```bash
astro dev restart
```




