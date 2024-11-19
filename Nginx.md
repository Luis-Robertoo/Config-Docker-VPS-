## [Pagina inicial](README.md)

# Instalando e configurando o NGINX.

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
