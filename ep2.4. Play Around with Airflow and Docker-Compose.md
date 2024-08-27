# Part A Install Astro and Play Around with Containers

## Step 1. Create a Virtual Environment

### Create the virtual environment and activate
```bash
python3 -m venv .venv
source .venv/bin/activate
```

## Step 2. Install apache-airflow 
```bash
pip install apache-airflow==2.10.0
```
## Step 3. Install Astro CLI
Link: https://www.astronomer.io/docs/astro/cli/install-cli?tab=linux#install-the-astro-cli

```bash
curl -sSL install.astronomer.io | sudo bash -s -- v1.28.1
```

## Step 4. Astro Dev 
```bash
astro dev init
```
```bash
astro dev start
```

## Step 5. Play Around with Containers
```bash
docker exec -it <webserver_container_name> /bin/bash
```
Or 
```bash
astro dev bash <webserver_container_name>
```



