+++
title = "instalando_docker_ce_debian"
description = ""
categories = []
tags = []
draft = true
date = "2017-03-31T17:28:50-03:00"

+++
Debian Jessie (8)

O repositório para instalar o Docker mudou, anteriormente era usado o apt.dockerproject.org. Agora é usado o mesmo hostname (download.docker.com) para todos as distribuições linux suportadas.


apt-get update

apt-get -y install \
  apt-transport-https \
  ca-certificates \
  curl \
  software-properties-common


curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -

add-apt-repository \
         "deb [arch=amd64] https://download.docker.com/linux/debian \
         $(lsb_release -cs) \
         stable"

apt-get update

apt-get -y install docker-ce

mkdir -p /etc/systemd/system/docker.service.d

cat > /etc/systemd/system/docker.service.d/environment.conf <<"EOF"
[Service]
EnvironmentFile=/etc/default/docker
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// $DOCKER_OPTS
EOF

Se estiver usando um kernel mais recente

add-apt-repository \
        "deb http://ftp.debian.org/debian jessie-backports main"

apt-get -t jessie-backports install linux-image-4.9.0-0.bpo.2-amd64

vim /etc/default/docker
[...]
DOCKER_OPTS="--dns 8.8.8.8 --dns 8.8.4.4 -s overlay2"
[...]
