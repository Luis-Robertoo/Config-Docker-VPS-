# CI-CD em VPS

## Aqui contem instruções para facilitar o deploy automatico em VPS ou VMs utilizando tecnologias como: GITHUB Actions, SSH, Docker.

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
* Deve ter um site simples rodando da porta 80.

****
## Removendo NGINX completamente.
* sudo systemctl stop nginx  (Parando o serviço)
* sudo apt-get purge nginx
* sudo apt-get autoremove
* sudo rm -rf /etc/nginx /var/log/nginx
* sudo systemctl status nginx (Verificando se o serviço foi extinto)
