# SuperVisor

## Driver Service

Reference driver endpoint service written in Falcon, Werkzeug, Psutil and Docker

[Find the repository here](https://hub.docker.com/r/t0xic0der/supervisor-driver-service)

<p align="center">
    <img src="https://img.shields.io/github/issues/t0xic0der/supervisor-driver-service?style=flat-square&logo=appveyor&color=teal">
    <img src="https://img.shields.io/github/forks/t0xic0der/supervisor-driver-service?style=flat-square&logo=appveyor&color=teal">
    <img src="https://img.shields.io/github/stars/t0xic0der/supervisor-driver-service?style=flat-square&logo=appveyor&color=teal">
    <img src="https://img.shields.io/github/license/t0xic0der/supervisor-driver-service?style=flat-square&logo=appveyor&color=teal">
    <img src="https://img.shields.io/github/watchers/t0xic0der/supervisor-driver-service?style=flat-square&color=teal&logo=appveyor">
</p>

## Note
This project works as an intuitive remotely accessible system performance monitoring and task management service for 
container station servers and headless Raspberry Pi setups where multiple containers are concurrently running and 
require observation, with secure passcode-protected endpoints so that clients can connect via the [SuperVisor Frontend 
Service](https://github.com/t0xic0der/supervisor-frontend-service/) and manage their devices.

## Features
- Zero dependence on pre-rendered template with the use of **DeadSync** to render DOM elements on connection
- Efficient JSON data structure for 100% faster updating with the use of **LiveSync** to refresh DOM contents
- Intuitive endpoints for fetching preliminaries, statistics, logs and process listing for containers
- Intuitive endpoints for fetching preliminaries and revision histories for images
- Intuitive endpoints for fetching preliminaries for both networks and volumes
- Relatively low overhead from the server during live stat (approx. 2MB over Python 3 runtime usage)
- Live polling time period is left at client-side decision to stick to a simple client-server model
- Monitoring station information is provided by the awesome **`psutil`** library
- Monitoring and management Docker information is provided by the effective **`docker-py`** library
- Added protection using passcode verification parameter check and server-side authentication of data requests
- Decoupled structure allows for connection to frontend service ([Check here](https://github.com/t0xic0der/supervisor-frontend-service))
- Authenticated process management endpoints - **`TERMINATE`**, **`KILL`**, **`SUSPEND`** and **`RESUME`** ops
- Rewritten entirely in Falcon WSGI and Werkzeug HTTP server to emphasise on speed, efficiency and cleaner code

## Usage

Run the following command if you are on a generic PC.

```
docker run -d \
  --restart unless-stopped \
  --name supervisor-driver-service \
  -p 8888:8888 \
  -p 6969:6969 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  t0xic0der/supervisor-driver-service:v1.1.0b-amd64
```

or the following command, if you are running an aarch64 distribution on Raspberry Pi 3 or 4.

```
docker run -d \
  --restart unless-stopped \
  --name supervisor-driver-service \
  -p 8888:8888 \
  -p 6969:6969 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  t0xic0der/supervisor-driver-service:v1.1.0b-arm64
```

Then, run the following command to grab the credentials.

```
docker logs supervisor-driver-service
```

```
 ,---.                    .    ,o               
 `---..   .,---.,---.,---.|    |.,---.,---.,---.
     ||   ||   ||---'|     \  / |`---.|   ||    
 `---'`---'|---'`---'`      `'  ``---'`---'`    
           |
 * Driver Service v1.1.0-beta
 * IP version        : 4
 * Passcode          : 6097A8C00A2BC97C
 * Sync URI          : http://0.0.0.0:8888/
 * TermSocket URI    : http://0.0.0.0:6969/
 * Monitor service   : Psutil v5.8.0
 * Container service : DockerPy v4.4.1
 * WebSocket service : Terminado v0.9.2
 * Endpoint service  : Falcon v2.0.0
 * HTTP server       : Werkzeug v1.0.1
 * Running on http://0.0.0.0:8888/ (Press CTRL+C to quit)
 * TermSocket started on port 6969
```

Take a note of _sync URI_, _termsocket URI_ and _passcode_ carefully and enter these at the login screen of the SuperVisor Frontend Service.

## Table of contents
1. [Home](https://github.com/t0xic0der/supervisor-driver-service/wiki)
2. [Installation](https://github.com/t0xic0der/supervisor-driver-service/wiki/Installation)
3. [Download releases](https://github.com/t0xic0der/supervisor-driver-service/releases)
4. [SuperVisor Frontend Service](https://github.com/t0xic0der/supervisor-frontend-service)

## Contribute
You may request for the addition of new features in the [issues](https://github.com/t0xic0der/supervisor-driver-service/issues) page but as the project is singlehandedly maintained - it might take time to develop on them. Please consider forking the repository and contributing to its development.