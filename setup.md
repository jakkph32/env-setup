sudo apt update && sudo apt upgrade -y --no-install-recommends && \
sudo apt install -y --no-install-recommends \
curl && \
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash && \
source ~/.bashrc && \
nvm install 14.17.0 && \
nvm use 14.17.0 && \
npm install -g npm@7.15.1 && \
npm install -g yarn@1.22.10 && \
npm install -g pnpm@10.4.1 && \
npm install -g typescript@4.3.5 && \
npm install -g eslint@7.31.0 && \
npm install -g prettier@2.3.2 && \
npm install -g @vue/cli@4.5.13 && \
npm install -g @nestjs/cli@8.0.0 && \
npm install -g @angular/cli@12.2.0 && \
npm install -g @nestjs/schematics@8.0.0 && \
npm install -g @angular-devkit/schematics-cli@12.2.0 && \
npm install -g @angular-devkit/build-angular@12.2.0 && \
curl -o- -fsSL https://get.docker.com && \
sudo sh docker.sh && \
sudo usermod -aG docker $USER && \
sudo systemctl enable docker && \
sudo systemctl start docker && \
sudo apt install -y --no-install-recommends \
docker-compose && \
sudo apt autoremove -y && \
sudo apt clean && \
sudo rm -rf /var/lib/apt/lists/* && \
sudo rm -rf /var/cache/apt/* && \
sudo rm -rf /var/cache/debconf/* && \
sudo rm -rf /var/cache/fontconfig/* && \
sudo rm -rf /var/cache/gdm/* && \
sudo rm -rf /var/cache/lightdm/* && \
docker volume create portainer_data >/dev/null
  $STD docker run -d \
    -p 8000:8000 \
    -p 9443:9443 \
    --name=portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    portainer/portainer-ce:latest
$STD docker run -d \
      -p 9001:9001 \
      --name portainer_agent \
      --restart=always \
      -v /var/run/docker.sock:/var/run/docker.sock \
      -v /var/lib/docker/volumes:/var/lib/docker/volumes \
      portainer/agent --server-host="tcp://host.docker.internal" --server-port
$STD docker run -d  && \
git clone https://github.com/jakkph32/env-setup.git && \
cd env-setup && \
docker-compose up -d && \
