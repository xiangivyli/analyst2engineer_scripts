# Port

- `localhost` is the loopback IP address [127.0.0.1](http://127.0.0.1/), equivalent to talking to my own computer server via network  
- `port` determines which service I would like to use, like calling out a specific number of one channel  

### List of TCP and UDP port numbers
https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers

The number ranges from 0 – 65535 like multiple different channels and is categorised into 𝐒𝐲𝐬𝐭𝐞𝐦 [0, 1023], 𝐑𝐞𝐠𝐢𝐬𝐭𝐞𝐫𝐞𝐝 𝐏𝐨𝐫𝐭𝐬  [1024, 49151], and 𝐓𝐞𝐦𝐩𝐨𝐫𝐚𝐫𝐲 𝐔𝐬𝐞𝐝 𝐏𝐨𝐫𝐭𝐬 [49152, 65535]. 

### Stream run
How to run your app: https://docs.streamlit.io/develop/concepts/architecture/run-your-app
```bash
streamlit run your_script.py
```

### Demo
### Option 1, pull an official image and add features in the docker-compose.yml
#### docker-compose.yml
```yml
version: '1.0'
services:
  streamlit:
    image: python:3.9
    command: bash -c "pip install -r /app/include/streamlit_container_requirements.txt && streamlit run --server.enableWebsocketCompression=false --server.enableCORS=false --server.enableXsrfProtection=false /app/include/streamlit_app.py"
    ports:
      - "8501:8501"
    volumes:
      - ./include:/app/include
```

### Option 2, build a customised image and simplify the docker-compose.yml
#### Dockerfile
```dockerfile
# Use the official Python image
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy the requirements file
COPY include/streamlit_container_requirements.txt .

# Install the dependencies
RUN pip install -r streamlit_container_requirements.txt

# Copy the application code
COPY app/ .

# Copy the data directory
COPY include/data /data

# Command to run the Streamlit app
CMD ["streamlit", "run", "--server.enableWebsocketCompression=false", "--server.enableCORS=false", "--server.enableXsrfProtection=false", "streamlit_app.py"]
```
#### docker-compose.yml
```bash
version: '1.0'

services:
  streamlit:
    build: .
    ports:
      - "8501:8501"
    volumes:
      - ./app:/app
      - ./include/data:/data
    environment:
      - STREAMLIT_ENV=development
```
