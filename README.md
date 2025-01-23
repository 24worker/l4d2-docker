# Left 4 Dead 2 Docker Server

This repository contains the necessary files to run a Left 4 Dead 2 server using Docker.

## File Descriptions

- `host.txt`: Contains information displayed in the top right corner of the server.
- `motd.txt`: Contains the message of the day displayed on the server's main page.
- `addons`: Directory for server plugins.
- `cfg`: Directory for server configuration files.
  - `server.cfg`: Main server configuration file. The `hostname` parameter in this file sets the server name.

## Language / 语言

- [English](#english)
- [中文](READMECN.md)

## English

### Prerequisites

- Docker CE installed
- Docker Compose installed

### Using Docker Compose

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/l4d2-docker-dev.git
    cd l4d2-docker-dev
    ```

2. Start the server using Docker Compose:
    ```sh
    docker-compose up -d
    ```

3. To stop the server:
    ```sh
    docker-compose down
    ```

### Using Docker CLI

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/l4d2-docker-dev.git
    cd l4d2-docker-dev
    ```

2. Build the Docker image:
    ```sh
    docker build -t l4d2server .
    ```

3. Run the container:
    ```sh
    docker run -d --name l4d2server -p 27015:27015 -p 27015:27015/udp -v $(pwd)/addons:/home/steam/l4d2server/left4dead2/addons -v $(pwd)/cfg/server.cfg:/home/steam/l4d2server/left4dead2/cfg/server.cfg:ro -v $(pwd)/host.txt:/home/steam/l4d2server/left4dead2/host.txt:ro -v $(pwd)/motd.txt:/home/steam/l4d2server/left4dead2/motd.txt:ro 24workers/l4d2server:latest -secure +exec server.cfg -port 27015 -tickrate 100
    ```

4. To stop the container:
    ```sh
    docker stop l4d2server
    docker rm l4d2server
    ```
