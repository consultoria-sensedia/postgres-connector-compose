# Docker-compose para Sensedia API Connector Postgres

Repositório com configuração para subir Sensedia API Connector para PostgreSQL.

```sh
#'cd' no diretório dos arquivos
#Configurar CONNECTOR_ID, CONNECTOR_FACTOR no .env

#subirá: 
# postgres (usuário, senha e banco padrão: database)
# sensedia/postgres-db-9.4-conn
# Ngrok (opcional, remova no docker-compose.yml se não precisar )
# Adminer (opcional, remova no docker-compose.yml se não precisar )

sudo docker-compose up 

#Se utilizando Ngrok, colar a url gerada no "endpoint" do Connector, no Manager.
```
No navegador:

http://localhost:4040 -> Interface do [Ngrok](https://ngrok.com/) (Ngrok exporta serviço localhost para URL pública, nessa url estarão todos os detalhes dele inclusive a **url pública** a ser colada no endpoint do Connector, no Manager)

http://localhost:8080 -> Interface do [Adminer](https://www.adminer.org/) (Ferramenta simples para administração, query, etc de BD)

## Customizações
No ```.env``` basta adicionar:

```
DB_PORT=porta do banco de dados PgSQL
DB_PASSWORD=senha do usuário do banco de dados PgSQL
DB_USER=usuário do banco de dados PgSQL
CONNECTOR_PORT=porta exposta pelo serviço do conector
```

Da forma como está no ```docker-compose.yml``` o banco de dados terá o mesmo nome do usuário (por padrão "database"), se for necessário alteração, basta acrescentar:

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
 
## Dica de utilização
Se for interessante que cada dev tenha seu banco local, pode ser criado um padrão para as configurações de banco (via variáveis de ambiente) e replicadas em um Connector por dev. As únicas configurações diferentes então serão o nome do Connector, CONNECTOR_ID, CONNECTOR_FACTOR e o endpoint (cada um apontando para a maquina de cada dev).

## Referências
[Documentação API Connectors](https://help.v3.apisuite.sensedia.com/pt/api-platform-guide/4.3.x.x/api-connectors/api-connectors.html)

[Imagem PqSQL Connector DockerHub](https://hub.docker.com/r/sensedia/postgres-db-9.4-conn)

[Imagem Postgres](https://hub.docker.com/_/postgres) no DockerHub

[Imagem Ngrok](https://hub.docker.com/r/wernight/ngrok) no DockerHub

[Imagem Adminer](https://hub.docker.com/_/adminer) no DockerHub

