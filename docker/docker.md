# Docker

- <a href="https://www.docker.com/" target="_blank">Docker</a>
- <a href="https://hub.docker.com/" target="_blank">Docker Hub</a>
- <a href="https://docker-curriculum.com/" target="_blank">Docker for Beginners</a>
- <a href="https://docker-curriculum.com" target="_blank">INTRODUCTION</a>

docker und docker composer version:

```
docker -v
docker-compose -v
```

List all processes:

```
docker ps
```

List all images:

```
docker image ls
```

Run a docker container with parameters:

- --name: the name of the container
- --rm: remove container when container was stopped
- -d: detached, so the console can be used for others
- -P: published ports

```
docker run --name mongo-dongo --rm -d -P mongo
```

Run a docker container with parameters:

- --name: the name of the container
- --rm: remove container when container was stopped
- -d: detached, so the console can be used for others
- -p: host-port:container-port

```
docker run --name mongo-dongo --rm -d -p 8888:80 mongo
```

## Medium

- <a href="https://rominirani.com/docker-on-windows-mounting-host-directories-d96f3f056a2c" target="_blank">Docker on Windows — Mounting Host Directories (aka Volumes)</a>

## Help

Usage: `docker [OPTIONS] COMMAND`

A self-sufficient runtime for containers

| Options                | Description                                                                    |
| ---------------------- | ------------------------------------------------------------------------------ |
| --config string        | Location of client config files (default "C:\\Users\\pro\\.docker")            |
| -D, --debug            | Enable debug mode                                                              |
| -H, --host list        | Daemon socket(s) to connect to                                                 |
| -l, --log-level string | Set the logging level                                                          |
|                        | ("debug" oder "info" oder "warn" oder "error" oder "fatal")                    |
|                        | (default "info")                                                               |
| --tls                  | Use TLS; implied by --tlsverify                                                |
| --tlscacert string     | Trust certs signed only by this CA (default "C:\\Users\\pro\\.docker\\ca.pem") |
| --tlscert string       | Path to TLS certificate file (default "C:\\Users\\pro\\.docker\\cert.pem")     |
| --tlskey string        | Path to TLS key file (default "C:\\Users\\pro\\.docker\\key.pem")              |
| --tlsverify            | Use TLS and verify the remote                                                  |
| -v, --version          | Print version information and quit                                             |

### Management Commands

| Management Commands | Description                   |
| ------------------- | ----------------------------- |
| config              | Manage Docker configs         |
| container           | Manage containers             |
| image               | Manage images                 |
| network             | Manage networks               |
| node                | Manage Swarm nodes            |
| plugin              | Manage plugins                |
| secret              | Manage Docker secrets         |
| service             | Manage services               |
| stack               | Manage Docker stacks          |
| swarm               | Manage Swarm                  |
| system              | Manage Docker                 |
| trust               | Manage trust on Docker images |
| volume              | Manage volumes                |

### Additional Commands

| Additional Commands | Description                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| attach              | Attach local standard input, output, and error streams to a running container |
| build               | Build an image from a Dockerfile                                              |
| commit              | Create a new image from a container's changes                                 |
| cp                  | Copy files/folders between a container and the local filesystem               |
| create              | Create a new container                                                        |
| diff                | Inspect changes to files or directories on a container's filesystem           |
| events              | Get real time events from the server                                          |
| exec                | Run a command in a running container                                          |
| export              | Export a container's filesystem as a tar archive                              |
| history             | Show the history of an image                                                  |
| images              | List images                                                                   |
| import              | Import the contents from a tarball to create a filesystem image               |
| info                | Display system-wide information                                               |
| inspect             | Return low-level information on Docker objects                                |
| kill                | Kill one or more running containers                                           |
| load                | Load an image from a tar archive or STDIN                                     |
| login               | Log in to a Docker registry                                                   |
| logout              | Log out from a Docker registry                                                |
| logs                | Fetch the logs of a container                                                 |
| pause               | Pause all processes within one or more containers                             |
| port                | List port mappings or a specific mapping for the container                    |
| ps                  | List containers                                                               |
| pull                | Pull an image or a repository from a registry                                 |
| push                | Push an image or a repository to a registry                                   |
| rename              | Rename a container                                                            |
| restart             | Restart one or more containers                                                |
| rm                  | Remove one or more containers                                                 |
| rmi                 | Remove one or more images                                                     |
| run                 | Run a command in a new container                                              |
| save                | Save one or more images to a tar archive (streamed to STDOUT by default)      |
| search              | Search the Docker Hub for images                                              |
| start               | Start one or more stopped containers                                          |
| stats               | Display a live stream of container(s) resource usage statistics               |
| stop                | Stop one or more running containers                                           |
| tag                 | Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE                         |
| top                 | Display the running processes of a container                                  |
| unpause             | Unpause all processes within one or more containers                           |
| update              | Update configuration of one or more containers                                |
| version             | Show the Docker version information                                           |
| wait                | Block until one or more containers stop, then print their exit codes          |

Run `docker COMMAND --help` for more information on a command.
