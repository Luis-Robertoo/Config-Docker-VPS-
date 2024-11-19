
## [Pagina inicial](../README.md)

# Exemplo de docker compose.

## O arquivo docker compose deve se chamar docker-compose.yaml, ele depende da identação, ela é necessária:

### Exemplo de arquivo que usa um dockerfile como ponto de partida

```yaml
version: 1
services: 
    nginx:
        build:
            dockerfile: ./docker/nginx.dockerfile
            context: .
        image: nginx
        container_name: container-lb
        environment:
            SENHA: "SenhaForte"
            LOGIN: ${LOGIN}
        ports:
            - "80:5000"
        depends_on:
            - "redis"
        volumes:
            - caminho/local:caminho/container
            - projeto/front/dist:/var/www/html
            
    redis:
        image: "redis:alpine"

```

* O container NGINX é baseado em um dockerfile.
* Configuramos a porta 5000 do container para a porta 80 do host.
* O container NGINX depende do container do Redis.
* Por meio do ${LOGIN} podemos passar via arquivo .env variaveis de ambiente para o docker-compose.