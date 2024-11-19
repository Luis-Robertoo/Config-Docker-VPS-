
## [Pagina inicial](../README.md)

# Exemplo de docker file.

## O arquivo docker file deve se chamar Dockerfile, sem extensão.

### Exemplo de dockerfile

```Dockerfile

# define a imagem base
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

# define a pasta de trabalho
WORKDIR /App

# copia tudo para a pasta App
COPY . ./

# restaura o projeto
RUN dotnet restore

# Builda e publica a solução
RUN dotnet publish -c Release -o out

# espoem a porta 5000
EXPOSE 5000

# define a imagem base que vai rodar o projeto
FROM mcr.microsoft.com/dotnet/aspnet:8.0

# define a pasta de trabalho
WORKDIR /App

# copia os arquivos de build para a pasta atual
COPY --from=build /App/out .

# Roda a aplicação
ENTRYPOINT ["dotnet", "{NOME-DA-APLICAÇÂO}.dll"]

```


## Comandos uteis

### FROM

Instrução obrigatória que indica qual imagem vai ser utilizada como ponto de partida. Podemos  criar uma imagem a partir de uma imagem do Linux com .NET instalada ou um sistema Linux usando uma imagem do Ubuntu e assim por diante. É possível criar sua própria imagem usando a instrução FROM scratch.

```Dockerfile
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
```
O comando acima indica que será criado uma imagem com .NET SDK 8.0
****

### WORKDIR

Define uma pasta dentro do container onde os comandos serão executados.

```Dockerfile
WORKDIR /App
```
****

### COPY e ADD

Comandos para copiar arquivos e pastas de um lugar específico na máquina local para uma pasta no container.

```Dockerfile
COPY . ./
```

Diferença é que ADD copia arquivos remotos para alguma pasta na imagem e também pode copiar arquivos compactados (tar.gz) que serão descompactados na imagem automaticamente.

Por questões de semântica, sempre utilize COPY para copiar arquivos e pastas locais e ADD para arquivos remotos ou compactados. Utilize o ADD se realmente for necessário. 
****

### RUN

Serve para executar comandos no processo de montagem da imagem que estamos construindo no Dockerfile, ele é executado durante o build (construção da imagem) e não durante a construção do container. Em um Dockerfile é possível ter mais de um comando RUN.

```Dockerfile
RUN dotnet restore
RUN dotnet publish -c Release -o out
```

Os comandos acima restaurão e publicam um projeto em .NET.
****

### CMD

Diferente do RUN, o CMD executa apenas na criação do container e não no build da imagem. Deve ser único no Dockerfile.

Ele pode ser substituido na linha de comando.

```
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
****

### ENTRYPOINT
Funciona parecido com o comando RUN. Pode conter varios parametros. Deve ser único no Dockerfile. Ele é estatico e não pode ser substituido na linha de comando. 

```Dockerfile
ENTRYPOINT ["dotnet", "{NOME-DA-APLICAÇÂO}.dll"]
```

Algo parecido com isso será executado quando o container executar:
```
dotnet {NOME-DA-APLICAÇÂO}.dll
```
****

### ENTRYPOINT vs CMD

Entrypoint e CMD só existem de forma separada para facilitar nossas vidas. Nada mais.

Quando um container é inicializado, o que será executado é a soma de Entrypoint e CMD.

```Dockerfile
ENTRYPOINT ["dotnet", "suaapp.dll"] 
CMD ["meuparametro"]
```

O resultado da execução é semelhante a: 
```
dotnet suaapp.dll meuparametro
```


