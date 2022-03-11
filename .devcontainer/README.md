# Setup and Run a Jupyter Lab Server

## Quickstart

### Jupyter Lab

1. Download the files into a directory, say `jupyter`:
    ```bash
    $ tree jupyter/
    jupyter
    ├── devcontainer.json
    ├── docker-compose.yml
    ├── Dockerfile
    └── README.md
    ```
1. (Optional) Change the default login token, `asdf`
1. Execute
    ```bash
    $ cd jupyter
    $ docker-compose up
    ```
1. In a web browser, open [https://127.0.0.1](https://127.0.0.1)

### VS Code

1. Download the files into a directory, say `jupyter/.devcontainer`:
    ```bash
    $ tree jupyter/.devcontainer
    jupyter/.devcontainer
    ├── devcontainer.json
    ├── docker-compose.yml
    ├── Dockerfile
    └── README.md
    ```
1. Open folder `jupyter` in VS Code: "File > Open Folder..."
1. Start remote container: "View > Command Palette..."
1. Start typing: "Remote-containers: Rebuild and Reopen in Container"
1. After startup completes (bottom left would say "Dev Container: Jupyter")
1. You can create and run Jupyter notebooks in VS Code as well as in Jupyter Lab at [https://127.0.0.1](https://127.0.0.1)


## Explanation of Files

### `Dockerfile`

[`Dockerfile`](Dockerfile) contains the instructions for building a [Docker image](https://docs.docker.com/engine/reference/builder/). [Any Jupyter compatible image](https://github.com/jupyter/docker-stacks/wiki) can be used on the `FROM` line. ([Dockerfile reference](https://docs.docker.com/engine/reference/builder/))

### `devcontainer.json`

File [`devcontainer.json`](devcontainer.json) is used by VS Code to facilitate [developing inside a container](https://code.visualstudio.com/docs/remote/containers). ([devcontainer reference](https://code.visualstudio.com/docs/remote/devcontainerjson-reference))

### `docker-compose.yml`

[`docker-compose.yml`](docker-compose.yml) specifies parameters for building and starting the server container instance. ([Docker compose reference](https://docs.docker.com/compose/)/ [Jupyter Docker image options](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/common.html))

* `SHELL=/bin/zsh` sets default shell inside Jupyter Lab as zsh.
* `JUPYTER_TOKEN=asdf` sets login token as `asdf`. If a password is set using the login screen, the server needs to be restarted in order for the new password to take effect.
