# Part A Install Astro and Play Around with Containers

## Step 1. Create a Virtual Environment

### Install Python 3.10 (Optional)
Deadsnakes PPA is a popular and trusted repository maintained by the Ubuntu community 
(Reference: https://www.geeksforgeeks.org/how-to-install-python-on-linux/)
```bash
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.10 python3.10-venv 
```

### Create the virtual environment and activate
```bash
python3.10 -m venv .venv
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

## Step 4. Astro Dev Init
```bash
astro dev init
```

## Step 5. Astro Dev Start
```bash
astro dev start
```

## Step 6. Play Around with Containers
```bash
docker exec -it <webserver_container_name> /bin/bash
```
Or **Dev Containers** extension: The Dev Containers extension lets you use a Docker container as a full-featured development environment.


