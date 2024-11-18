# CI-CD em VPS

## Aqui contem algumas instruções para facilitar a configuração e o deploy em um VPS ou VMs utilizando tecnologias como: GITHUB Actions, SSH, Docker.

### Informações necessarias para iniciar:

* Maquina VPS ou VM com IP publico
* Conexão SSH aberta.

### Passos

1. Criar chaves SSHs no seu computador.
2. Inserir na VM a chave SSH publica criada.
3. Criar chaves SSHs na VM.


****
## Instalando NGINX.
* sudo apt update
* sudo apt install nginx
* sudo apt-get install ufw (instalando firewall)
* sudo ufw allow 22/tcp (liberando firewall)
* sudo ufw allow 80/tcp (liberando firewall)
* sudo ufw allow 443/tcp (liberando firewall)
* sudo ufw enable (iniciando firewall)
* Reinicialize a VM.
* Deve ter um site simples rodando da porta 80.

****
## Configuração basica NGINX.
* cd /var/www (Pasta com os web sites estaticos - usar o SUDO para editar)
* cd /etc/nginx/sites-enabled (Pasta com as configurações - usar o SUDO para editar)
* sudo service nginx restart (Reinicia o NGINX para usar as novas configurações)

****
## Removendo NGINX completamente.
* sudo systemctl stop nginx  (Parando o serviço)
* sudo apt-get purge nginx
* sudo apt-get autoremove
* sudo rm -rf /etc/nginx /var/log/nginx
* sudo systemctl status nginx (Verificando se o serviço foi extinto)

****
## Instalando Docker na maquina.
* sudo apt-get update
* sudo apt-get install ca-certificates curl
* sudo install -m 0755 -d /etc/apt/keyrings
* sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
* sudo chmod a+r /etc/apt/keyrings/docker.asc
* echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
* sudo apt-get update
* sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
* sudo docker run hello-world
* sudo groupadd docker
* sudo usermod -aG docker $USER
* newgrp docker
* docker run hello-world
* ****
* **Ativar Docker Engine ao iniciar a maquina**
* sudo systemctl enable docker.service
* sudo systemctl enable containerd.service
* ****
* **Desativar Docker Engine ao iniciar a maquina**
* sudo systemctl disable docker.service
* sudo systemctl disable containerd.service
