# Docker-compose para Sensedia API Connector Postgres

Repositório com configuração para subir Sensedia API Connector para PostgreSQL.

```sh
#'cd' no diretório dos arquivos
#Configurar CONNECTOR_ID, CONNECTOR_FACTOR no .env

#subirá: 
# postgres (usuário, senha e banco padrão: database)
# sensedia/postgres-db-9.4-conn
# Ngrok (opcional)
# Adminer (opcional)

sudo docker-compose up 

#Se utilizando Ngrok, colar a url gerada no "endpoint" do Connector, no Manager.
```
No navegador:

http://localhost:4040 -> Interface do [Ngrok](https://ngrok.com/) (Ngrok exporta serviço localhost para URL pública, nessa url estarão todos os detalhes dele inclusive a **url pública** a ser colada no endpoint do Connector, no Manager)

http://localhost:8080 -> Interface do [Adminer](https://www.adminer.org/) (Cliente BD)

## Customizações
No ```.env``` basta adicionar:

```
DB_PORT=porta do banco de dados PgSQL
DB_PASSWORD=senha do usuário do banco de dados PgSQL
DB_USER=usuário do banco de dados PgSQL
CONNECTOR_PORT=porta exposta pelo serviço do conector
```

Da forma como está no ```docker-compose.yml``` o banco de dados terá o mesmo no do usuário, se for necessário alteração, basta acrescentar:

```
      POSTGRES_DB: ${DB_NAME}
```
 em 
 
 ```
 services: 
  postgres:
    environment:
 ```
 e **DB_NAME** no ```.env```, além de qualquer outra variável de ambiente disponível na [Imagem Postgres](https://hub.docker.com/_/postgres) no DockerHub.

## Referências
[Documentação API Connectors](https://help.v3.apisuite.sensedia.com/pt/api-platform-guide/4.3.x.x/api-connectors/api-connectors.html)

[Imagem PqSQL Connector DockerHub](https://hub.docker.com/r/sensedia/postgres-db-9.4-conn)

[Imagem Postgres](https://hub.docker.com/_/postgres) no DockerHub

[Imagem Ngrok](https://hub.docker.com/r/wernight/ngrok) no DockerHub

[Imagem Adminer](https://hub.docker.com/_/adminer) no DockerHub

