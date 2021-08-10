<h1 align="center"> Web_terraform </h1> <br>

<p align="center">
  A simple web service based on a microservice architecture
</p>


## Table of Contents

- [Introduction](#introduction)
- [Requirements](#requirements)
- [Quick Start](#quick-start)

## Introduction

A simple web service based on a microservice architecture (golang for backend and Vue.js for frontend) for running terraform scripts online.


## Requirements
The application can be run locally or in a docker container, the requirements for each setup are listed below.

### Local
* [Golang latest](https://golang.org/dl/)
* [Node.js latest](https://nodejs.org/en/)

### Docker
* [Docker](https://www.docker.com/get-docker)


## Quick Start

### Configure Acess data for databases

The default value in the __http.ListenAndServe__ file is set to connect to postgreSQL with user `postgres` and password `qwerty` on port `5433`. For mongoDB with user `mongo` and password `qwerty` on port `27018`. Default port on web server `8080`.

### Run Local

Build golang server:
```bash
$ cd ./backend/
$ go build -o server
```
Run golang server:
```bash
$ ./server
```
Golang server will run by default on port `8090`. To change the port on golang server, you can edit __http.ListenAndServe__ im __main.go__. The default value in the __http.ListenAndServe__ for server port is `8090`.

:
Next work with Node.js serverInstall requirements for no:
```bash
$ cd ./forntend
$ npm install
```
Run Node.js server:
```bash
$ npm run serve --port 8080
```
Node.js server will run by default on port `8090`. You can change default port.
### Run Docker

Build the golang image:
```bash
$ docker build -t terraform-server .
```

When ready, run it:
```bash
$ docker run -p 8090:8090 terraform-server
```
Application will run by default on port `8090`


Build the frontend image:
```bash
$ docker build -t vue-server .
```

When ready, run it:
```bash
$ docker run -p 8080:8080 vue-server
```
Application will run by default on port `8080`

If you want to run `both` servers on the same machine, use __Docker Compose__.

##Screenshot
