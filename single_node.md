# Single Node for Learning

## Setup

```
sudo apt update && sudo apt upgrade
sudo apt install curl
curl https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa1JRdl82Zk9fR1dVV1JjMUhGU2FuM0pkaExDZ3xBQ3Jtc0ttaFdFSVRBbkR1SHlQNlhJYlZxSERrU3V3QXFEbWstVnFMNE0yczFSaG44ajJ2OFNOODdVNWFIZVM3QnpvdVpKNXNyLW9USk1zMGI4aWtKQW4tcmJNQU5RdTFKLW4ybFNBQkt6SC1iOXhkMG9GMWlXRQ&q=https%3A%2F%2Freleases.rancher.com%2Finstall-docker%2F20.10.sh&v=uBgMbO0c9a4  | sh

sudo usermod -aG docker $USER && newgrp docker
sudo docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher

```
