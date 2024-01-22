#!/bin/bash
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce -y
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
chmod +x ~/.docker/cli-plugins/docker-compose
sudo mkdir ~/jenkins
sudo chmod 666 ~/jenkins
sudo usermod -aG docker $USER
sudo systemctl start docker
sudo systemctl enable docker
sudo chmod 666 /var/run/docker.sock
docker volume create --name=grafana_folder
docker volume create --name=mysql-storage
docker volume create --name=grafana_storage
docker volume create --name=grafana_datasources
docker volume create --name=grafana_dashboard
sudo chgrp 1001 /var/lib/docker/volumes/grafana_folder/_data
sudo chgrp 1001 /var/lib/docker/volumes/mysql-storage/_data
sudo chgrp 1001 /var/lib/docker/volumes/grafana_storage/_data
sudo chgrp 1001 /var/lib/docker/volumes/grafana_datasources/_data
sudo chgrp 1001 /var/lib/docker/volumes/grafana_dashboard/_data
sudo chmod g+w /var/lib/docker/volumes/grafana_folder/_data
sudo chmod g+w /var/lib/docker/volumes/mysql-storage/_data
sudo chmod g+w /var/lib/docker/volumes/grafana_storage/_data
sudo chmod g+w /var/lib/docker/volumes/grafana_datasources/_data
sudo chmod g+w /var/lib/docker/volumes/grafana_dashboard/_data
