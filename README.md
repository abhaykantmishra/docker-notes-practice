# Docker Notes

## Docker Components
### 1. Docker Image -
    Similar to a recipibook that list ingridients and instructions for a recipi.

    Lighweight, Standalone, Executable package that includes everything that are needed to run a software including the code, runtime, lib, system-tool, os.

### 2. Docker Container -
    This is the main recipi that we are going to serve.

    Runable Instance, It represents execution enviroment for application including code, runtime, system-tool, lib yhat are in docker image.

    We can run multiple containers(instances) from a single image.

### 3. Docker Volume  -
    Persistance Data Storage Mechanism that allows data to share b/w a docker container and the host machine or even among multiple containers.

    Shared storage outside the container.


### 4. Docker Network -
    Communication channel that enables different Docker conainers to talk to each other or with external world.

    Allow containers to share information while maintaining isolation.

    Big resturent kitchen several chef working on different recipies, chefs can communicate, exchange ingridients & share recipies.

## Docker Workflow
### 1. Docker Client -
    User-interface for interacting with docker.

    Tool to give Docker the commands.Chef giving instruction to kitchen staff.

    > docker run myapp
    > docker build myapp

### 1. Docker Host (Docker Deamon) -
    Background process responsible for managing conatiner on host system.

    ~ Listen for docker cmd
    ~ Create & Manages docker containers
    ~ Build images
    ~ Handle other docker related tasks

### 3. Docker Registery (Docker-Hub) -
    Centerlize repository for docker images.

    It is a recipi library containing different recipies.

    ~ Host both public and private registories or packages
    ~ Similar as git & github

## How To Create Docker Image
- ### It starts with a special file called ***`Dockerfile`***.
- ### It is a set of instruction.
### Some Commands for `Dockerfile` 
- #### ***FROM:*** Specify the base image
    ```bash
    From image[:tag] [AS name]
    # Example
    FROM ubuntu:24.04
    ```
- #### ***WORKDIR:***  Working directory
    ```bash
    WORKDIR /path/to/workdir
    # Example
    WORKDIR /app
    ```
- #### ***COPY:*** Copy files and dir from build context to the image  
    ```bash
    COPY [--chown=<user>:<group>] <src>... <dest>
    # Example
    COPY . /app
    ```
- #### ***RUN:*** Excecute cmd during image build
    ```bash
    RUN <command>
    # Example
    RUN npm run dev
    ```
- #### ***EXPOSE:*** Informs docker that the conatiner listen on specified port at runtime
    ```bash
    EXPOSE <port> [<port>/<protocol>...]
    # Example
    EXPOSE 3000
    ```
- #### ***ENV:*** Sets enviroment variable during the build process
    ```bash
    ENV KEY=VALUE
    # Example
    ENV NODE_ENV=production
    ```
- #### ***ARG:*** Define build time variables
    ```bash
    ARG <name>[=<default value>]
    # Example
    ARG NODE_VERSION=20
    ```

- #### ***VOLUME:*** Creates a mount-point for external mounted volumes 
    ```bash
    VOLUME ["/data"]
    # Example
    VOLUME /myvol
    ```
- #### ***CMD:*** Default commads to execute when the container tart 
    ```bash
    CMD ["executable", "param1", "param2"]
    CMD ["param1", "param2"]
    # Example
    CMD ["npm" "run" "dev"]
    CMD npm run dev
    # CMD & ENTRYPOINT
    # CMD - flexible, can be overridden
    # ENTRYPOINT - can't be overridden
    ```
