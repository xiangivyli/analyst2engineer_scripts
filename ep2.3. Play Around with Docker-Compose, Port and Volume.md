# Port

- `localhost` is the loopback IP address [127.0.0.1](http://127.0.0.1/), equivalent to talking to my own computer server via network  
- `port` determines which service I would like to use, like calling out a specific number of one channel  

### List of TCP and UDP port numbers
https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers

The number ranges from 0 – 65535 like multiple different channels and is categorised into 𝐒𝐲𝐬𝐭𝐞𝐦 [0, 1023], 𝐑𝐞𝐠𝐢𝐬𝐭𝐞𝐫𝐞𝐝 𝐏𝐨𝐫𝐭𝐬  [1024, 49151], and 𝐓𝐞𝐦𝐩𝐨𝐫𝐚𝐫𝐲 𝐔𝐬𝐞𝐝 𝐏𝐨𝐫𝐭𝐬 [49152, 65535]. 

### Stream run
How to run your app: https://docs.streamlit.io/develop/concepts/architecture/run-your-app
How to deploy streamlit using Docker: https://docs.streamlit.io/deploy/tutorials/docker
```bash
streamlit run your_script.py
```

### Demo
#### 1. Structure of the project
```
├── docker-compose.yml
├── include
│   ├── data.csv
│   └── streamlit_app.py
└── streamlit_app
    ├── Dockerfile
    └── requirements.txt
```
#### /include
##### data.csv
```csv
year,career
2011,biology
2012,biology
2013,biology
2014,biology
2015,biology
2015,pathology
2016,pathology
2017,pathology
2018,pathology
2018,database_manager
2019,database_manager
2020,database_manager
2021,business_analytics
2022,business_analytics
2023,business_analytics
2024,data_engineer
```
##### streamlit_app.py
```python
import streamlit as st
import pandas as pd

# Load data from CSV file
data_file_path = '/app/include/data.csv'
df = pd.read_csv(data_file_path)

# Streamlit App
st.title("Streamlit Application")
st.write("Ivy's journey:")
st.dataframe(df, width=800, height=600)
```
#### /streamlit_app
##### Dockerfile
```Dockerfile
# Use the official Python image
FROM python:3.8-slim

# Set the working directory inside the container
WORKDIR /app

# Copy requirements.txt and install dependencies
COPY ./requirements.txt /app
RUN pip install -r requirements.txt

# Expose the streamlit port
EXPOSE 8501

# Run the streamlit app
ENTRYPOINT ["streamlit", "run", "/app/include/streamlit_app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```
##### requirements.txt
```txt
streamlit==1.33.0
pandas==2.0.0
```

#### Volume Option 1
##### `docker run`
`docker run -d -p 8501:8501 -v /workspaces/demo/include:/app/include streamlit_app:1.0`

#### Volume Option 2
###### docker-compose.yml
```yml
name: demo

services:
  streamlit_app:
    build:
      context: ./streamlit_app
      dockerfile: Dockerfile
    ports:
      - "8501:8501"
    volumes:
      - ./include:/app/include
```

#### Command docker-compose commands
##### Start Services
`docker-compose up -d`

#### Stop Services
`docker-compose stop`

#### Restart Services
`docker-compose start`

#### Remove Services
`docker-compose down`

