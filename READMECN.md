# 求生之路2 Docker 服务器

本项目基于 [HoshinoRei](https://github.com/HoshinoRei/l4d2server-docker) 的工作。

这个仓库包含使用 Docker 运行求生之路2服务器所需的文件。

## 文件说明

- `host.txt`: 包含显示在服务器右上角的信息。
- `motd.txt`: 包含显示在服务器主页面的每日信息。
- `addons`: 插件文件夹。
- `cfg`: 服务器配置文件夹。
  - `server.cfg`: 主要的服务器配置文件。此文件中的 `hostname` 参数设置服务器名称。

## 先决条件

- 已安装 Docker CE
- 已安装 Docker Compose

## 使用 Docker Compose

1. 克隆仓库：
    ```sh
    git clone https://github.com/yourusername/l4d2-docker-dev.git
    cd l4d2-docker-dev
    ```

2. 使用 Docker Compose 启动服务器：
    ```sh
    docker-compose up -d
    ```

3. 停止服务器：
    ```sh
    docker-compose down
    ```

## 使用 Docker CLI

1. 克隆仓库：
    ```sh
    git clone https://github.com/yourusername/l4d2-docker-dev.git
    cd l4d2-docker-dev
    ```

2. 构建 Docker 镜像：
    ```sh
    docker build -t l4d2server .
    ```

3. 运行容器：
    ```sh
    docker run -d --name l4d2server -p 27015:27015 -p 27015:27015/udp -v $(pwd)/addons:/home/steam/l4d2server/left4dead2/addons -v $(pwd)/cfg/server.cfg:/home/steam/l4d2server/left4dead2/cfg/server.cfg:ro -v $(pwd)/host.txt:/home/steam/l4d2server/left4dead2/host.txt:ro -v $(pwd)/motd.txt:/home/steam/l4d2server/left4dead2/motd.txt:ro 24workers/l4d2server:latest -secure +exec server.cfg -port 27015 -tickrate 100
    ```

4. 停止容器：
    ```sh
    docker stop l4d2server
    docker rm l4d2server
    ```
