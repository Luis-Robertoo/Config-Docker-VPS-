
## [Pagina inicial](README.md)

# Acessando uma máquina por meio do protocolo SSH.

## Informações necessarias para iniciar:

* Maquina VPS ou VM com IP publico
* Conexão SSH aberta (PORTA 22).

### Passos

* Criar chaves SSHs no seu computador.
    * Windows (PUTTY)
        * PUTTY gera chaves .PPK
        * Iniciar o PUTTYgen
        * Gerar as chaves
        * Salvar as chaves
        * Inicie o PUTTY
        * Vá até Connection > SSH > Auth > Credentials
        * Adicione a chave privada.
        * Vá até Session no topo.
        * Coloquei o HostName seguindo esse exemplo: hostname@ip
        * Salve e teste.

    * LINUX (SSH) é nativo.
        * Gera chaves .PEM
        * No terminal digite: "ssh-keygen -t ed25519"
        * No terminal digite: "ssh -i /path/NOME-DA-SUA-CHAVE.pem hostname@ip"




