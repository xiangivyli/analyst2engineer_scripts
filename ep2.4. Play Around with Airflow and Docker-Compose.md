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



