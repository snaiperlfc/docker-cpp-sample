# docker-cpp-sample

## Using docker-compose

> :information_source: The docker-compose file in this repository uses the latest [compose specification](https://docs.docker.com/compose/compose-file/), which was introduced with docker-compose version 1.27.0+. Please make sure to use an up-to-date docker-compose version.

> :information_source: The Docker required is 20.10.16+

To stand-up a complete Camunda Platform 8 Self-Managed environment locally the [docker-compose.yml](docker-compose.yml) file in this repository can be used.

The full environment contains these components:
- Zeebe
- Connectors
- Operate
- Identity
- Elasticsearch
- Keycloak

Clone this repo and issue the following command to start your environment:

The POCO C++ Libraries are powerful cross-platform C++ libraries for building network- and internet-based applications that run on desktop, server, mobile, IoT, and embedded systems.

The POCO C++ Libraries source code is on [GitHub](https://github.com/pocoproject/poco).

[Install POCO](https://pocoproject.org/download.html)

Run the following command to build:
```
conan install conanfile.txt --build missing
cd ./src
docker build -t docker-cpp-sample .
```

The following command to start your environment:

```
docker-compose up -d
```
Wait a few minutes for the environment to start up and settle down. Monitor the logs, especially the Keycloak container log, to ensure the components have started.

Now you can navigate to the different web apps and log in with the user `demo` and password `demo`:
- Operate: [http://localhost:8081](http://localhost:8081)
- Identity: [http://localhost:8084](http://localhost:8084)
- Elasticsearch: [http://localhost:9200](http://localhost:9200)

Keycloak is used to manage users. Here you can log in with the user `admin` and password `admin`
- Keycloak: [http://localhost:18080/auth/](http://localhost:18080/auth/)

The workflow engine Zeebe is available using gRPC at `localhost:26500`.

To tear down the whole environment run the following command

```
docker-compose down -v
```