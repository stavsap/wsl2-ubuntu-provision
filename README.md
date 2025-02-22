# WSL2 Ubuntu Distro Provision

For advanced configurations, check this links:

- [wsl config on the host](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#wslconfig).

- [wsl per instance config](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#wslconfig).

### Update

```shell
sudo apt update
sudo apt upgrade -y
sudo apt autoremove -y
```

#### Install dev tools

```shell
sudo apt-get install git tree nano ca-certificates curl gnupg lsb-release make build-essential linux-tools-common python3-venv python3-pip -y

```

Setup git and ssh, change to your `email` and `username`.
 

```shell
git config --global user.email "< EMAIL >"
git config --global user.name "< USERNAME >"
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519 -N ""
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

#### Install Docker CE

 
```shell
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
sudo groupadd docker || true
sudo usermod -aG docker $USER
newgrp docker

```

#### [brew](https://brew.sh/)

 
```shell

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

```
