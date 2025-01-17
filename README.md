# Linux Setup

## Google Chrome
```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```
```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Visual Studio Code

```bash
wget https://go.microsoft.com/fwlink/?LinkID=760868 -O code.deb
```

```bash
sudo dpkg -i code.deb
```

### VS Code settings

```JSON
{
  "telemetry.enableTelemetry": false,
  "telemetry.enableCrashReporter": false,
  "editor.minimap.enabled": false,
  "terminal.integrated.fontFamily": "MesloLGS NF",
  "editor.mouseWheelZoom": true,
  "terminal.integrated.fontSize": 12,
  "terminal.integrated.mouseWheelZoom": true,
  "terminal.integrated.cursorStyle": "line",
  "workbench.colorTheme": "One Dark Pro Mix",
  "workbench.iconTheme": "eq-material-theme-icons-light",
  "workbench.productIconTheme": "material-product-icons",
  "files.autoSave": "afterDelay",
  "editor.fontLigatures": true,
  "editor.fontFamily": "FiraCode Nerd Font",
  "editor.tabSize": 2,
  "editor.smoothScrolling": true,
  "editor.wordWrap": "on",
  "editor.cursorBlinking": "expand",
  "editor.cursorSmoothCaretAnimation": "on",
  "terminal.integrated.copyOnSelection": true,
  "terminal.integrated.cursorBlinking": true,
  "terminal.integrated.rightClickBehavior": "paste",
  "terminal.integrated.smoothScrolling": true
}
```

## Git

```bash
sudo apt install git
```

## 1Password

```bash
wget https://downloads.1password.com/linux/debian/amd64/stable/1password-latest.deb -O 1password.deb
```

```bash
sudo apt install curl
```

```bash
sudo apt install gnupg2
```

```bash
sudo dpkg -i 1password.deb
```

## zsh and Oh-My-ZSH

Verify that zsh is installed or not

```bash
zsh --version 
```

```bash
sudo apt install zsh
```

Return which shell is the default one

```bash
echo $SHELL 
```

Change the default shell to zsh

```bash
chsh -s $(which zsh) 
```

:exclamation: **Log out of current session and log back in**

Install Oh My ZSH

```bash
sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)" 
```

## Powerlevel10k

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Restart ZSH

```bash
exec zsh 
```

For the config wizard

```bash
p10k configure 
```

## Terraform

```bash
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
```

```bash
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

```bash
sudo gpg --no-default-keyring --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg --fingerprint
```

```bash
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```

```bash
sudo apt update
```

```bash
sudo apt install terraform
```

## GitHub CLI

```bash
type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

## Google Cloud SDK

```bash
curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-467.0.0-linux-x86_64.tar.gz
```

```bash
tar -xf google-cloud-cli-467.0.0-linux-x86_64.tar.gz
```

```bash
./google-cloud-sdk/install.sh
```

## Docker Installation

make sure old versions are not installed

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

Installing pre-req

```bash
sudo apt-get update && sudo apt-get install ca-certificates curl gnupg -y
```

GPG Key and Repo setup

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

```bash
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

installation

```bash
sudo apt-get update
```

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```bash
docker --version
```

Use as non-root user

```bash
sudo groupadd docker
```

```bash
sudo usermod -aG docker $USER
```

## NodeJS NPM & NVM

```bash
curl -fsSL https://deb.nodesource.com/setup_19.x | sudo -E bash - && sudo apt-get install -y nodejs
```

or to install it via NVM

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```
