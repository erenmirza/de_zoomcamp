# Docker

- Docker delivers software in packages called containers
- Containers are isolated from one another and bundle their own software, libraries and config files
- Containers can communicate with each other through well-defined channels

## Why do we need Docker?

- **Isolation**
    - Docker containers isolate applications from each other and the host system
    - Prevents conflicts between different applications
    - Simplifies troubleshooting 
- **Reproducible environments**
    - Docker images capture an application's exact dependencies
    - Ensures that the same environment exists in development, testing, and production 
- **Faster deployment**
    - By packaging applications as containers, deployment becomes significantly faster
    - Containers can be quickly spun up and scaled on demand
- **Portability**
    - Docker containers can run on any system with Docker installed
    - Enables seamless movement of applications across different servers and cloud providers 
- **Collaboration**
    - Docker facilitates sharing applications and their environments with other developers
    - Promotes collaboration and easier team workflows 


## Installing Docker

[Tutorial Video](https://www.youtube.com/watch?v=kaQQVoEBumY)

To run Docker on Windows, there’s few ways. You can either run it using the Docker legacy Hyper-V backend, or you can use WSL 2 which offers much better performance and stability.

### What is Windows Subsystem for Linux (WSL2)?

The Windows System for Linux (WSL) lets you run a Linux environment directly on windows without needing to use virtual machines or dualboot setup. This allows you to fully take advantage of Linux directly on your Windows machine. Its faster and it consumes less resources than running a virtual machine. 

Its integrated, meaning that you can directly access all your files on your Windows machine.

If you’re planning to run Docker on Windows, then its highly recommended you use WSL 2 for your Docker Desktop backend as users can leverage Linux workspaces and avoid having to maintain both Linux and windows build scripts. 

It also provides a much faster experience when using Docker. Without WSL 2, just starting docker takes almost up to minute, while with WSL 2, it takes less than 10 seconds.

1. Open powershell as administrator
1. Run `wsl --install`
1. Restart computer
1. Set a username and password
1. Create a .wslconfig file in C:/Users/{username}
1. Paste the following
    1. Code snippet
        ```
        [wsl2]
        memory=4GB
        processors=2
        ```


1. Download and run docker installer
1. Restart computer
1. Install wsl VSCode extension

## Using Docker Example

1. Create Dockerfile
1. Paste following
    1. Code snippet
        ```
        FROM python:3.9

        RUN pip install pandas

        WORKDIR /app
        COPY pipeline.py pipeline.py

        ENTRYPOINT [ "python", "pipeline.py" ]
        ```
1. Create a file pipeline.py
1. In terminal `docker build -t test:pandas .`
1. In terminal `docker run -it test:pandas`