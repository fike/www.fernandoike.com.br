+++
title = "Instalando Docker CE no Debian"
description = "Instalação do Docker Community Edition 17.03 no CentOS"
categories = ["devops", "docker", "portugues"]
tags = ["docker", "devops", "linux", "centos", "systemd"]
draft = true
date = "2017-03-31T17:28:50-03:00"

+++
A Docker mudou o nome dos seus produtos e o *Docker Engine* agora é conhecido como **C**ommunity **E**dition. Se ainda não leu a respeito, você pode ler pequeno resumo que escrevi sobre a mudança no "*[Docker pronto para o mundo corporativo](https://www.fernandoike.com.br/2017/03/30/docker-pronto-para-o-mundo-corporativo/)*". Uma outra mudança para fazer a instalação a instalação mudou, para instalar as versões anteriores era usado o **packages.docker.com** e a partir da versão 17.03 o repositório é **download.docker.com**.

Este mini tutorial usa como base o [Debian Jessie](https://www.debian.org/releases/jessie/) e é ligeiramente modificado do roteiro de instalação da [documentação oficial](https://docs.docker.com/engine/installation/linux/centos/) do Docker CE Stable. Há uma outra pequena diferença é que aqui foi usado o usuário *root* e também a instalação de um arquivo adicional da configuração do Docker no [Systemd](https://www.freedesktop.org/wiki/Software/systemd/).


## Removendo versões anteriores

Se houver um repositório Docker já configurado, lembre-se de remover ele e também o pacote docker que não seja do repositório da Docker e suas dependências. Exemplo: O pacote Docker encontrado no Debian **é docker.io**
```
#apt-get remove docker.io
```

## Configurando o repositório

O repositório da Docker usa HTTPS e para usá-lo é necessário adicionar o pacote **apt-transport-https**, o **software-properties-common** permite gerenciar os repositórios sem ter editar manualmente os arquivos.
```
#apt-get update

#apt-get -y install \
  apt-transport-https \
  ca-certificates \
  curl \
  software-properties-common
```

Baixando a chave GPG do repositório Docker e adicionando o repositório .
```
#curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -

#add-apt-repository \
         "deb [arch=amd64] https://download.docker.com/linux/debian \
         $(lsb_release -cs) \
         stable"
```

Instalando o pacote Docker Community Edition.
```
#apt-get update

#apt-get -y install docker-ce
```

A versão kernel Linux padrão da Jessie é bem antigo (3.16), se quiser usar uma versão mais recente poderá instalar via [Backports](https://backports.debian.org/). No momento em que este mini tutorial estava sendo escrito a versão mais atual disponível era 4.9, esta versão foi removido o patch do AUFS e não tem uma versão do módulo dele no Backports para instalar. Portanto, para usar o Docker com um kernel Linux recente e na Jessie terá que modificar os parâmetros de inicialização do serviço Docker no Systemd.

Para adicionar ou alterar algum parâmetro de inicialização Docker via Systemd, alguns tutoriais dizem para alterar o arquivo **docker.service** nos diretórios "**/usr/lib/systemd/system**" ou "**/lib/systemd/system**". Minha sugestão é fazer isso em outro local, porque numa eventual uma atualização do pacote do Docker, o arquivo pode ser sobrescrito e você perder as alterações feitas para iniciar o serviço do Docker. Exemplo: **/etc/systemd/system/**"


#mkdir -p /etc/systemd/system/docker.service.d

#cat > /etc/systemd/system/docker.service.d/environment.conf <<"EOF"
[Service]
EnvironmentFile=/etc/default/docker
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// $DOCKER_OPTS
EOF

#systemctl daemon-reload

#add-apt-repository \
        "deb http://ftp.debian.org/debian jessie-backports main"

#apt-get update

#apt-get -t jessie-backports install linux-image-4.9.0-0.bpo.2-amd64

#vim /etc/default/docker
[...]
DOCKER_OPTS="-s overlay2"
[...]

#reboot
