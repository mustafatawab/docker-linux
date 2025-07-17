**Docker Version**
```
docker --version
```

**Pull Image**
```
docker pull baseImage
```
```
e.g docker pull hello-world
```

**List of Docker Images**
```
docker images | docker image ls
```

Running Container List
```
docker ps | docker container ls
```

All Containers List
```
docker ps -a | docker container ls -a
```

**Build Image** Which is place in the current directory
```
docker build -t imageName:tag .  | docker build -f Dockerfile imageName:tag .
``` 
```
docker build -t my-dev-image .
```

**Run Container** <br>
First 8000 port is for out mechine where the container will be running and second 8000 port is inside the container where our containerized will  be running.
```
docker run -d -p 8000:8000 imageName:tag | docker run -d --name my-container -p 8000:8000 imageName


# Interactive Mode
docker run -it -p 8000:8000 imageName:tag /bin/bash
```
 
     
**Test the container**
```
docker run -it --rm my-dev-image /bin/bash -c "poetry run pytest"
```



**Inspect Image**
```
docker inspect my-dev-image
```


**Container Logs**
```
docker logs my-container
```


**Interact with the container**
```
docker exec -it my-container /bin/bash
```







**Dockerfile Syntax**
```
LABEL maintainer="ameen-alam"
# Set the working directory in the container
WORKDIR /code
# Install system dependencies required for potential Python packages
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Poetry
RUN pip install poetry

# Copy the current directory contents into the container at /code
COPY . /code/

# Configuration to avoid creating virtual environments inside the Docker container
RUN poetry config virtualenvs.create false

# Install dependencies including development ones
RUN poetry install

# Make port 8000 available to the world outside this container
EXPOSE 8000

# Run the app. CMD can be overridden when starting the container
CMD ["poetry", "run", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--reload"]

```